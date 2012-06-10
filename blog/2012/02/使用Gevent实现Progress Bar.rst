:title: 使用Gevent实现Progress Bar
:slug: 使用gevent实现progress-bar
:url: http://www.adieu.me/blog/2012/02/使用gevent实现progress-bar/
:published_on: 2012-02-13 01:21:00

周末有时间，打算给 `xunlei <https://github.com/adieu/xunlei>`_ 实现下载时的Progress Bar，以便用户在远程服务器上下载时可以随时了解当前下载的进度以及下载速度。

Progress Bar的实现方法大致可以分为两种:

1. 显式更新
2. 同步更新

显式更新的方法很容易理解，即在当前任务进行的过程中，每隔一段时间更新一次Progress Bar的进度。对于下载任务来说，可以设计为每下载多少个字节，即更新一次进度。显式更新的方法有两个弊端，一是需要让已有任务主动调用，就涉及到如何让一个原本连续执行的任务停下来的问题，特别是对底层函数的调用，不能直接通过修改源码的方式实现。二是当更新Progress Bar进度时，其实是停止了任务的执行，对任务的执行效率有一定影响。

同步更新的方法应当是更加理想的选择。即在任务执行的过程当中，同时更新任务进度。但Python的Thread却不是那么给力。由于GIL的影响造成的性能损失不容忽略。

还好有最近很火的 `Coroutine <http://en.wikipedia.org/wiki/Coroutine>`_ 存在，使用Coroutine可以很容易实现Thread的效果，速度还刷刷的快。真乃居家旅行杀人越货之良伴啊。

这里简单贴一点代码片段出来，更详细的更新见 `这个commit <https://github.com/adieu/xunlei/commit/4d4622bfc6344effefafbd0a3837b484b4e4e976>`_

.. sourcecode:: python

  download = gevent.spawn(self.download, url=url, filename=filename)
  update_progress = gevent.spawn(display_progress_bar, filename=filename, size=size)
  download.link(update_progress)
  gevent.joinall([download, update_progress])

.. sourcecode:: python

  def display_progress_bar(filename, size):
      """Display progress bar while downloading"""
      from gevent.greenlet import LinkedExited
      width = 32
      last_size = 0
      try:
          while True:
              if os.path.isfile(filename):
                  current_size = os.path.getsize(filename)
                  percentage = current_size*100/size
                  current_width = width*percentage/100
                  sys.stderr.write('% 3d%% [%s%s] %s/s    \r' % (percentage, '#'*current_width, ' '*(width-current_width), filesizeformat(current_size - last_size)))
                  last_size = current_size
              time.sleep(1)
      except LinkedExited:
          sys.stderr.write('100%% [%s]\n' % ('#'*width))

简单来说，就是先用gevent生成download和update_progress这两个greenlet。download负责下载，update_progress负责更新Progress Bar。然后告诉download，让它在执行完毕时通知update_progress。最后让这两个greenlet同时执行。display_progress_bar函数会每秒更新一次当前进度，直到收到download执行完成的通知。通知是以LinkedExited异常的形式来传递的。

从这个例子可以看出，在许多Python需要同步执行的场合，使用Coroutine都可以更加简洁高效的完成。Python程序员应当把Coroutine纳入到自己的弹药库储备中来。
