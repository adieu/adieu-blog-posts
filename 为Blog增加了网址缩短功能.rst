:title: 为Blog增加了网址缩短功能
:slug: 为Blog增加了网址缩短功能
:url: http://www.adieu.me/blog/2011/01/为Blog增加了网址缩短功能/
:published_on: 2011-01-07 08:00:42.213592

`之前 <http://www.adieu.me/blog/2010/08/%E7%BB%99Blog%E5%A2%9E%E5%8A%A0%E4%BA%86%E5%90%8C%E6%AD%A5%E5%88%B0Twitter%E7%9A%84%E5%8A%9F%E8%83%BD/>`_ 添加了当博客有新文章发布的时候会自动发送更新到Twitter的功能。由于偷懒，发送的网址并没有缩短，导致今天出现了标题过长时超过Twitter字数限制的问题。

花了一些时间，使用 `django-shorturls <https://github.com/jacobian/django-shorturls>`_ 为博客添加了简单的网址缩短功能，之后就不用害怕标题太长导致Twitter无法更新的问题了，并且发送到Twitter的更新也更加简洁。

其实，这是一个测试 :)