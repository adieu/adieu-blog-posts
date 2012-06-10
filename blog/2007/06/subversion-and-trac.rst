:title: 在media temple的dv中安装subversion和trac
:slug: subversion-and-trac
:url: http://www.adieu.me/blog/2007/06/subversion-and-trac/
:published_on: 2007-06-12 00:17:13.000001

在linux下尤其是远程的CentOS系统下安装subversion和trac可不是那么件轻松的活，摸索了半天时间，总算是搞好了。

参考了以下网站：

- http://blog.hellm.com/post/5
- http://alexle.net/archives/138
- http://elsid.net/2007/05/07/setup-svn-server-on-media-temple-dv-or-centos-with-plesk/
- http://elsid.net/2007/05/16/setup-trac-on-media-temple-dv-or-centos-with-plesk-installations/

安装过程大致是从yum到subversion到trac，其中media temple自带的subversion虽然版本不是最新的，也不影响正常使用，可以跳过subversion的安装，直接配置apache的svn处理页面。
另外由于trac的最新版本有了比较大的改进，所以安装过程以trac0.11dev的安装说明为准。

本想做个step by step教程的，但是想到明天早上还要早起和人开会，还是早点睡觉为好。
