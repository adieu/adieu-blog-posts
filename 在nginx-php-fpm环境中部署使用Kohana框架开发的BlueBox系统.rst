:title: 在nginx+php-fpm环境中部署使用Kohana框架开发的BlueBox系统
:slug: 在nginx-php-fpm环境中部署使用Kohana框架开发的BlueBox系统
:url: http://www.adieu.me/blog/2011/01/在nginx-php-fpm环境中部署使用Kohana框架开发的BlueBox系统/
:published_on: 2011-01-07 06:40:22

前两天想研究一下BlueBox这个新的FreeSwitch网页管理客户端系统，花了一点时间部署了一套。期间遇到了Nginx环境和Kohana框架兼容的问题，以下是遇到的问题以及解决的方案。

背景知识：
==========

* `Nginx <http://nginx.net/>`_ ：一款高效的Http服务器
* `Kohana <http://kohanaframework.org/>`_ ：一款PHP框架
* `BlueBox <http://www.2600hz.org/>`_ ： 使用Kohana开发的一款FreeSwitch网页管理客户端系统，前身是 FreePBX v3

问题及解决方案：
================

BlueBox的安装参见其相关文档，这里就不重复了。在安装流程中，进行到访问 *http://YOUR_WEB_SERVER/bluebox/* 这一步进行初始化时报错。系统会将页面转向到 *http://YOUR_WEB_SERVER/bluebox/index.php/installer* 这个页面，但是Nginx提示404页面无法找到，无法继续。

经过一番研究之后发现Kohana框架对Apache的支持比较好，在bluebox根目录下也有.htaccess 这个Apache的配置文件。BlueBox的安装文档也是基于Apache环境来编写的。从出错提示来看，应该是直接在index.php后面跟/installer导致Nginx将index.php/installer整体当成了脚本文件名在目录中寻找，最终无法找到，返回404错误。而Apache似乎会将index.php/installer打断，定位到index.php脚本，所以安装流程得以顺利进行。

找到问题之后首先尝试让BlueBox使用Nginx能够解析的url形式，由于并没有Kohana框架的使用经验，简单查看配置文件及Kohana的代码后没有发现解决问题的办法。一番Google以后，找到了 `这篇文档 <http://forum.kohanaframework.org/discussion/1505/x>`_ 。按照文档中的配置写法，修改了VirtualHost配置，使得Nginx能够正常兼容Kohana框架，问题得到解决。以下是我的配置文件，仅供参考：

.. sourcecode:: nginx

  server {
      listen       80;
      server_name  YOUR_DOMAIN;
      index        index.html index.htm index.php;
      root         /DOCUMENT_ROOT;

    location ~ .*\.(php|php5)?$ {
        fastcgi_pass  127.0.0.1:9000;
        fastcgi_index index.php;
        include fcgi.conf;
      }

    location /bluebox/ {
      rewrite index.php(.+)$ /bluebox/index.php?kohana_uri=$1 last;
    }
  }

其中php-fpm的部分与正常的在Nginx中部署php程序的配置一致，不需要多说，主要是在后面的rewrite rule中处理了index.php与/installer分离的问题。最近多次使用了nginx的rewrite以及try_files，越发觉得nginx在这方面的强大。

当Kohana与Nginx的兼容问题得到解决以后，剩下的安装流程就一切顺利。只是进入BlueBox之后一看，觉得功能还是稍显简单，估计需要再经过一定时间的开发之后，才能真正让人用的顺手。在那之前，我还是继续使用直接修改配置文件的方法来进行FreeSwitch的配置吧。
