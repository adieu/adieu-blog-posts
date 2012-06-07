:title: Install Wordpress
:slug: install-wordpress
:url: http://www.adieu.me/blog/2006/12/install-wordpress/
:published_on: 2006-12-26 07:53:31.000001

之前使用过Wordpress，这次也是驾轻就熟。不过更注重一些细节。在这里做一下记录，希望将来可以给别人做一下参考。

获得Wordpress最新版本
=====================

考虑了一下是使用最新的stable release还是直接从svn中获得alpha版本的代码。最后决定麻烦一下自己，采取在本地用svn保持最新的版本，然后上传的形式。

获得最新版本的方法这里不多说，将来可以专门做一下version                control方面的介绍。我使用的是windows下的TortoiseSVN。操作相对来说很简单，从Wordpress的源http://svn.automattic.com/wordpress/trunk/中同步最新的代码到本地就可以了。

上传Wordpress至虚拟主机
=======================

没什么好说的，ftp慢慢传吧。要想效率高，可以考虑使用phpzip，上传压缩文档在服务器端解压。我把wordpress放在了/blog目录下。

初始化
======

浏览www.adieu.cn/blog/，系统会提示没找到数据库连接，要求新建数据库连接。整个过程非常的智能化。中间填入数据库设置，一路next                step就可以了。数据库初始化完成之后会自动生成admin账号和随机密码。用这个账号登陆后台就可以开始配置了。

配置
====

其实也没什么好配置的，从网上下载一个自己喜欢的theme，然后安装上一些常用plugin就可以开博了。

我的plugin list `在此 <http://www.adieu.cn/blog/2006/12/hello-world/>`_ 。
