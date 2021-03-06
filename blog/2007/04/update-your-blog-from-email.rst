:title: 用Email更新Blog
:slug: update-your-blog-from-email
:url: http://www.adieu.me/blog/2007/04/update-your-blog-from-email/
:published_on: 2007-04-05 16:34:34.000003

总算搞定Email更新了，记一篇作为今天的更新。

可能只有很少的人会想用Email来更新自己的Blog，但是对于一个使用网络不方便或者随时随地想更新自己Blog的人来说，Email更新是一个很不错的选择。我们可以在手机上写Email，然后使用GPRS发送，这样写Blog再也没有了时间和地点的限制。

更新的方法我找到了两种，如下：

Wordpress内置的Email更新
========================

Wordpress从1.X版本开始就有了使用Email更新的功能，但是设置起来还是比较麻烦，详细的设置说明可以参考官方的设置说明， `在这里 <http://codex.wordpress.org/Blog_by_Email>`_ 。这里简单介绍一下几个阶段。

在Wordpress后台设置Email更新
----------------------------

设置的地址在Options->Writing，如图

.. image:: http://farm1.static.flickr.com/235/446966705_aa36b3bb41_o.jpg

Mail Server中填入你的Email邮件服务器地址。Login Name中填入登录名。Password当然就是密码了。Default mail category是Email更新的默认分类。

上面的提示告诉你最好将Email地址设成比较怪异的名字，以免收到spam的时候直接更新出来。不过按照官方的说明，最新的版本会效验Email是不是注册用户发过来的来避免spam，所以这里可以随意设置了。

新建邮箱地址
-------------

这是官方说明文档中的一步，其实就是使用上面的登录名和密码去新建一个邮箱。这步没什么好说的。

设置邮箱检查的触发器
----------------------

名字比较绕口，其实很简单。因为Wordpress不知道什么时候该去检查你的邮箱，所以你需要设定一个检查邮箱的触发器。这个步骤还比较原始，可能在将来会有所改进。官方提供了3种方法。

1. 手工访问http://yourwebdomain/installdir/wp-mail.php。就是在你发好Email之后手工触发一次。程序会去收信然后完成更新。
2. 使用WP-Cron WP-Mail插件。WP-Cron插件可以定期的去访问wp-mail.php完成更新。
3. 使用Server上的Cron Job。在Server上设定定期执行的脚本，定期访问wp-mail.php完成更新。

总结
----

总的来说，现在Wordpress提供的Email更新功能还比较原始。用户需要手动设定触发器（我就是忘了设定这个才更新失败的）。更重要的是，现在还不支持中文Email。查看了代码，发现里面还没有中文解码部分。总之，现在Wordpress的Email更新功能还不够完善，希望将来会有Update。

使用BlogMailr来更新
===================

既然Wordpress自带的Email更新功能不好用，我们只能寻求第三方的解决方案了。 `Lifehacker <http://lifehacker.com/software/blogging/update-your-blog-from-anywhere-via-email-213855.php>`_ 向我们推荐了 `BlogMailr <http://www.blogmailr.com/>`_ 。在注册之后就可以设定自己的Blog地址了，如图：

.. image:: http://farm1.static.flickr.com/247/446985861_0392be5f84_o.jpg

操作起来很简单，添加你的Blog（需要输入用户名和密码，存在风险）。然后BlogMailr会生成一个随机的邮箱地址。将你的Email地址加入到Valid  Sender之后，就可以向BlogMailr提供的邮箱发邮件来更新了。经过测试，效果很完美。更新成功之后还会发Email给你确认。

使用BlogMailr更新是 `Layer <http://www.adieu.me/blog/2007/03/layer/>`_ 的又一次成功。BlogMailr在用户和Wordpress之间加入了一层，解决了中文解码和更新触发的问题。虽然这项服务使用的人不多，但是这个思路值得大家借鉴。

如果大家有更好的Email更新Blog方案，欢迎推荐。
