:title: Zope and Plone
:slug: zope-and-plone
:url: http://www.adieu.me/blog/2007/03/zope-and-plone/
:published_on: 2007-03-30 02:35:05.000004

先从Wikipedia查两个定义。

Zope
  Zope是一个开源的web应用服务器，主要用python写成。它是一个事务型的对象数据库平台。

Plone
  Plone是一种开源的内容管理系统（CMS）。基于Zope，用Python写成。

有点绕，对吧。简单来说，Plone是一款基于Zope开发的内容管理系统，可以让用户管理各种类型的文档，数据。在插件的支持下，Plone还可以实现知识管理，协同办公，项目管理等。而且这一切都是免费的。

Plone在最新一次的CMS评比中位列第三，落后于PHP+MYSQL开发的Joomla和Drupal。他们的对比介绍可以参看 `这篇文章 <http://news.csdn.net/n/20061222/99787.html>`_ 。

内容管理系统（CMS）在国外已经是很普通的概念了，但是在国内从事相关工作的人还不多，普通人对其接受的程度也还比较低。以Plone为例，搜索了一下国内的信息，找到了这些：

- `中国ZOPE用户组 <http://www.czug.org/>`_
- `Plone空间 <http://plonespace.net/>`_
- `上海润普 <http://zopen.cn/>`_
- `北京新选择 <http://www.newchoice.org.cn/>`_

内容管理系统稍加定制就可以作为企业内部管理系统来使用，新选择在这块做了不少的工作，他们的产品也以开源的形式发布。如果对企业管理平台有兴趣，可以去看看他们的demo。

如果中国中小企业的IT应用水平能够不仅仅停留在修修电脑，弄弄网络的程度，相信这些开源的产品会有更大的发展空间。

今天在Ubuntu下安装了Zope 2.10.3＋Plone 3.0 beta。走了不少弯路，记录一下，也许别人遇到一样问题的时候可以Google到这篇文章。

- Ubuntu默认没有安装GCC，因为安装Zope的时候需要编译，所以要首先安装GCC
- 编译Zope还需要header文件的支持，所以需要先安装libc-dev，python-dev。这点浪费了我很多时间，因为没有安装libc-dev，编译的时候一直报错。
- Zope的安装过程请参考 `http://www.plope.com/Books/2_7Edition/InstallingZope.stx <http://www.plope.com/Books/2_7Edition/InstallingZope.stx>`_
- 如果make的时候提示不能编译，出现gcc error之类的提示，请检查libc-dev是否安装。
- 在新建instance时候用root用户似乎会有点问题，我是重新建了一次
- Plone的安装相对比较简单，按照下载包里的提示一步一步操作就可以了。Plone默认是自带i18n支持的，不过部分界面还需要进一步汉化。
