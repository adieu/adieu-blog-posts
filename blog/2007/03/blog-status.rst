:title: [Weekend Project]#2 Blog Status
:slug: blog-status
:url: http://www.adieu.me/blog/2007/03/blog-status/
:published_on: 2007-03-18 02:25:03.000006

又到了周末时间，本周的Weekend Project是Blog状态统计。

目标
====

自从开始写Blog之后，每天的生活增加了一项内容：跟踪每天的访问情况。查 `Google Analytics <http://www.google.com/analytics>`_，查 `Feed Burner <http://www.feedburner.com/>`_，查 `Technorati <http://www.technorati.com/>`_ 。虽然数字小的可怜，但是每天还是会乐此不疲的一天查好几次。

Wordpress有好几个插件提供统计信息的查询，但是尝试下来不是很理想。说句题外话，如果有哪家网站提供状态统计的整合后输出报表，我想我会使用。

还好的是通过写一点简单的程序可以满足自己的需要，我想实现以下功能：

- 同时从多个网站获取数据。比如：Feedburner，Technorati等。
- 提供RSS输出。能够订阅。
- 支持多用户。分享是一件美好的事情。

规划
====

开始写程序之前做点简单的规划可能会少走弯路。

- 使用Python来实现
- 尽量运用已经存在的module，减少编码难度。我只是想实现一个功能，而不是想去研究中间的技术是如何实现的
- Test Driven Development。很早就研究了这个理论，今天实践一下。
- 记录整个过程

Action
======

寻找参考资料
------------

互联网是强大的。

- `Feedburner API <http://www.feedburner.com/fb/a/developers/awapi>`_ 。使用Api可以从Feedburner获取订阅的信息。
- `Technorati API <http://www.technorati.com/developers/api/>`_ 。看起来Technorati的API要复杂一些。
- Google Analytics API。厄，竟然不存在。但是 `有人 <http://www.thinkingphp.org/2006/06/19/google-analytics-php-api-cakephp-model/>`_ 已经用模拟用户提交的方式，变相实现了部分API。
- Technorati API的Python封装。有好几个，`这个 <http://www.myelin.co.nz/technorati_py/>`_ 看起来比较强大。
- `RSS生成器 <http://www.dalkescientific.com/Python/PyRSS2Gen.html>`_ 。让我手动构造RSS，我可不干。
- Python的TDD资料。这个很早就看过了。

创建项目环境
------------

很简单，创建一个SVN控制的目录，把搜集到的几个module拷贝过去。

Coding
------

TDD之前没实践过，只能摸着石头过河了。

经过N小时的Coding，基本有了第一个可用的版本，`在这里 <http://adieu.googlecode.com/svn/trunk/project/blog-status/>`_ 。`源代码 <http://adieu.googlecode.com/svn/trunk/project/blog-status/>`_ 已经在Google  Code中管理起来了。

第一版功能还比较弱，只实现了从Feedburner中获取数据生成RSS Feed的功能。但是在写程序的过程中，积累了很多只有在实战中的经验。比如：

- TDD的编程方法在思维模式上和直接写代码有比较大的变化，初次尝试还不是很习惯
- 在unittest的testcase中，测试函数需要以test开头，Test是不认的。在这点上耽搁了不少时间。
- 对于这种简单脚本，其实用TDD的开发方式效率太低，不过大型系统写测试还是必要的。
- cgi脚本的调试比较麻烦。需要注意几个细节：
  - 脚本权限要是755
  - 脚本第一行要指定Python解析器地址
  - 源码最好用unix格式，windows可能会有兼容性问题

继续改进代码
------------

第一版的代码比较简单，还有一些feature没有实现。包括，整合technorati统计，错误处理等。由于时间关系，先放一下，等最近这段忙完了继续修改。

总结
====

好久没写代码了，效率很低，最后能做到什么程度心里也没底。不过看着最终的代码，心情还是比较畅快的。也许不以写程序为生的程序员都能够比较快乐吧。

PS：如果有朋友需要这种简单的feedburner->rss服务，请给我email，我很乐意把你的地址加入到现在的代码中。由于现在用的虚拟主机跑的python不能连接到数据库，抱歉没法提供自动注册的功能，只能采取这种比较笨的方法。
