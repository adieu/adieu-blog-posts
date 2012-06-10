:title: 使用 Google Books API 获取图书信息
:slug: 使用-Google-Books-API-获取图书信息
:url: http://www.adieu.me/blog/2010/07/使用-Google-Books-API-获取图书信息/
:published_on: 2010-07-19 15:05:09

Google Books 索引了大量的图书信息。当我们在开发和图书有关的应用时，可以使用开放的 `Google Books API`_ 方便的获取图书信息。

以下的代码片段简单演示了使用 `gdata-python-client`_ 进行搜索及图书信息获取的方法。

.. sourcecode:: python

	from gdata.books.service import BookService
	
	# 生成一个service实例
	client = BookService()
	# 做一次搜索
	results = client.search('google')
	# 遍历所有搜索结果
	for book in results.entry:
	    print book.title.text
	
	# 获取一本图书的详细信息
	one_book = client.get_by_google_id(results.entry[0].get_google_id())
	# 当获取单本图书信息的时候，介绍信息会更加详细
	print one_book.description.text
	# 当不习惯atom的处理方式时，使用to_dict()是一个好选择
	print one_book.to_dict()

详细的使用方法请参照API文档以及gdata库的源代码。当增加了用户认证部分的代码后，还可以实现对用户收藏的书籍列表进行管理的功能，提供了更多的mashup可能性。

.. _Google Books API: http://code.google.com/apis/books/
.. _gdata-python-client: http://code.google.com/p/gdata-python-client/