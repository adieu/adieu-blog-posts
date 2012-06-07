:title: Blog系统更新
:slug: Blog系统更新
:url: http://www.adieu.me/blog/2011/04/Blog系统更新/
:published_on: 2011-04-08 08:38:00.804053

Blog系统使用的是 `allbuttonspressed <http://www.allbuttonspressed.com/projects/allbuttonspressed>`_ 。这是一款运行在Google Appengine上的开源的简易CMS系统。之前根据自己的需要修改了部分源代码，我部署的版本则停留在了去年5月份左右。这两天花了一些时间将Blog系统更新到最新的版本。

在更新的过程中，发现merge最新的代码产生了不少conflict。为了将来merge的时候变得更加轻松，我修改了部分自定义代码，尽量采取注入式的修改，而不直接修改源代码。

现在，更新后的版本已经上线。从前台几乎看不出区别，后台底层还是有蛮大区别的。
