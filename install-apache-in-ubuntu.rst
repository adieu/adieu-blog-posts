:title: 在Ubuntu中安装Apache
:slug: install-apache-in-ubuntu
:url: http://www.adieu.me/blog/2007/01/install-apache-in-ubuntu/
:published_on: 2007-01-16 22:33:27.000001

安装Ubuntu是一件惬意的事情，在Ubuntu中安装Apache也是一件轻松的事情。但是，让Apache按照预期来运行，让我的cgi脚本跑起来不出错确让我费尽了心思。花了两天的时间总算明白了其中的奥妙。

由于是第一次接触Ubuntu，中间走了不少弯路，所以这里仅仅列一个最优安装过程的清单。

Ok, let's go!

Objective:
==========

我的目标是让Ubuntu中的Apache能够和我Windows中的Apache一样运行就可以了。其实要求很简单，能够处理简单的html，能够正常运行cgi就可以了。

Step by Step:
=============

1. 从新立得软件包管理器中安装apache2。当然在终端中运行sudo apt-get install apache2也可以达到效果。一切安装过程都是自动化完成的。
2. 安装完成之后，默认情况下apache已经开始运行了，打开Firefox，输入localhost看看效果。如果可以看到Apache/2.0.55 (Ubuntu) Server at localhost Port 80的字样，证明apache已经在正常运作了。
3. 默认情况下，apache的配置文件在/etc/apache2/下，www root在/var/www/下。我们可以把自己的网站拷贝到www root下，然后开始修改apache的配置。
4. apache配置文件夹下的文件说明在/etc/apache2/README中有很详细的介绍。感觉在Ubuntu中，apache的配置文件是分散在各个文件之中的。然后通过apache2.conf引用所有的配置文件。而在windows下，基本是一个httpd.conf解决所有问题。正是由于这样的转变，让我走了不少的弯路。我的配置过程相对来说很简单。
5. 编辑apache2.conf，去掉AddHandler cgi-script .cgi前面的注释。
6. (Important!)拷贝/mods-available/cgi.load 到/mods-enabled/下。
7. 编辑/sites-enabled/000-default，修改DocumentRoot为你的网站的目录。为这个目录的Options增加+ExecCGI这个选项，这样cgi脚本才会执行。
8. 重新启动apache，使用指令sudo /usr/sbin/apache2ctl -k restart。
9. 编辑你的cgi脚本，把第一行改为脚本解析器的路径，如果是python脚本的话，则应该为#!/usr/bin/python。
10. 给你的cgi脚本赋予读取和运行的权限。
11. 在firefox中浏览，如果正常显示则代表配置成功。如果失败，则检查/var/log/apache2/error.log。可能出现以下几种情况：

  - Options ExecCGI is off in this directory。请检查第七步
  - Permission denied。请检查第六步和第十步。

当然，在配置过程中出现的问题远远超出了本文所列的情况，很多时候还是需要自己根据错误提示来做很多相应的调整。

What's More:
============

写到这里，发现里面有赚钱的机会。一个对linux下配置apache很熟悉的人，完全可以将自己的经验作为产品来出售。当别人在配置中出现问题的时候，可以通过网络联络专家，咨询问题，同时付出一部分的费用。我相信对于时间比钱更重要的那一部分人来说，与其自己在那里摸索，找到一个专家，迅速解决自己的问题，显然是很划算的。当然，也有一部分人，比如说我，热衷于自己寻找问题的答案，并且在寻找问题解决方案的过程中获得乐趣，这些人就不是这项服务的潜在用户了。想想还真是“生命在于折腾”。
