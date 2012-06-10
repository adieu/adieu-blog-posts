:title: 使用Python导出WordPress数据
:slug: 使用Python导出WordPress数据
:url: http://www.adieu.me/blog/2010/12//
:published_on: 2010-12-16 10:29:12.766822

在进行Blog迁移的时候，需要从之前的WordPress系统中导出以往写的博文，导入新系统中。WordPress本身提供了信息导出的功能，但是使用xmlrpc接口来进行博文导出将会更加方便。

网上搜索了一下， `wordpress-library <http://code.google.com/p/wordpress-library/>`_ 提供了api简单的封装，不过直接使用Python自带的xmlrpclib来操作也非常的简单。代码片段如下：

.. sourcecode:: python

  import xmlrpclib

  XMLRPC_ENDPOINT = "http://www.YOURBLOG.com/xmlrpc.php"
  USERNAME = "YOURUSERNAME"
  PASSWORD = "YOURPASSWORD"
  BLOGID = "0" # Blog ID,如果是单用户的WordPress系统，则为0

  client = xmlrpclib.ServerProxy(XMLRPC_ENDPOINT)
  posts = client.metaWeblog.getRecentPosts(BLOGID, USERNAME, PASSWORD, 1000) # 最后一个参数代表取多少篇博文，如果想一次性获取全部博文，则将这个参数设为一个大数即可

  for post in posts:
      print post
      DO_SOMETHING_ELSE()

需要注意的是，返回的post所带的wp_slug参数是经过quote了的，需要unquote来得到原始的值，代码片段如下：

.. sourcecode:: python

  import urllib
  slug = urllib.unquote(post['wp_slug']).decode("utf8")

使用WordPress的xmlrpc接口还可以方便的进行其他操作，所有接口函数列表可以使用 ``mt.supportedMethods()`` 函数获得，如下：

.. sourcecode:: python

  >>> client.mt.supportedMethods()
  ['wp.getUsersBlogs', 'wp.getPage', 'wp.getPages', 'wp.newPage', 'wp.deletePage', 'wp.editPage', 'wp.getPageList', 'wp.getAuthors', 'wp.getCategories', 'wp.getTags', 'wp.newCategory', 'wp.deleteCategory', 'wp.suggestCategories', 'wp.uploadFile', 'wp.getCommentCount', 'wp.getPostStatusList', 'wp.getPageStatusList', 'wp.getPageTemplates', 'wp.getOptions', 'wp.setOptions', 'wp.getComment', 'wp.getComments', 'wp.deleteComment', 'wp.editComment', 'wp.newComment', 'wp.getCommentStatusList', 'wp.getMediaItem', 'wp.getMediaLibrary', 'wp.getPostFormats', 'blogger.getUsersBlogs', 'blogger.getUserInfo', 'blogger.getPost', 'blogger.getRecentPosts', 'blogger.getTemplate', 'blogger.setTemplate', 'blogger.newPost', 'blogger.editPost', 'blogger.deletePost', 'metaWeblog.newPost', 'metaWeblog.editPost', 'metaWeblog.getPost', 'metaWeblog.getRecentPosts', 'metaWeblog.getCategories', 'metaWeblog.newMediaObject', 'metaWeblog.deletePost', 'metaWeblog.getTemplate', 'metaWeblog.setTemplate', 'metaWeblog.getUsersBlogs', 'mt.getCategoryList', 'mt.getRecentPostTitles', 'mt.getPostCategories', 'mt.setPostCategories', 'mt.supportedMethods', 'mt.supportedTextFilters', 'mt.getTrackbackPings', 'mt.publishPost', 'pingback.ping', 'pingback.extensions.getPingbacks', 'demo.sayHello', 'demo.addTwoNumbers']

对这些接口函数的解析可以参考本文最后的相关链接，这里就不详细解释了。充分利用这些接口函数可以实现定制WordPress客户端，自动发帖等更加高级的功能，为开发者留下了无限的可能。

相关链接：
----------

* `XML-RPC Support « WordPress Codex <http://codex.wordpress.org/XML-RPC_Support>`_
* `XML-RPC wp « WordPress Codex <http://codex.wordpress.org/XML-RPC_wp>`_
* `representations » Programmatic Interfaces: the MovableType XMLRPC API <http://infinite-sushi.com/2005/12/programmatic-interfaces-the-movabletype-xmlrpc-api/>`_
