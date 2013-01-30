:title: Setup Go devlopment environment on Mac
:slug: setup-go-devlopment-environment-on-mac
:url: http://www.adieu.me/blog/2013/01/setup-go-devlopment-environment-on-mac/
:published_on: 2013-01-31 01:21:00

Recently I got some free time to have some taste of `Go <http://golang.org>`_.
And the first thing I wanted to do was to setup the Go development environment on my Mac.
Actually it turned out to be quite easy. Here is what I did:

Install Go
==========

The most convenient way of installing Go is through homebrew. One simple command:

.. sourcecode:: console

  $ brew install go

And you're ready to go.

The $GOPATH magic
=================

Before reading any documentation from Go, I was a little bit curious about how a static
type language like Go could manage its dependencies and packages. C didn't do very well
in this area and that's one reason I'm always trying to avoid writing C code directly.

I think the designer of Go share the same feeling with me and they made installing 3rd
party packages really easy with Go. For example, if you wants to install one package
from github, you could just use:

.. sourcecode:: console

  $ go get github.com/user/project

And Go support BitBucket, Google Code as well.

Actually you don't really have to install packages manually, you could simply import
them in your code by:

.. sourcecode:: go

  import "github.com/user/project"

And when you run your program, Go will automatically install all 3rd party packages
for you. Nice, isn't it?

Another good thing I find is that Go ask you to write your code in packages and you
have to put package declaration infront of your source code, like:

.. sourcecode:: go

  package name

That's what I like as a Python developer. I found package based development made my
life much easier to write high quality and testable code.

The whole package management experience is a little bit too magic for me. I'd like to
know how things work internally. After reading some documents and doing some experiment,
I found the magic, the $GOPATH environment variable.

The $GOPATH environment variable holds a directory tells Go where all package source
code lives and where to install 3rd party packages. And it holds all compiles libraries
too. It's like the standard directory structure to organize your Go project.

Since you could point $GOPATH to different directories, you could easily switch your
project environment when you work on different projects.

Virtualenv based Go project environment
=======================================

Sure, I could add $GOPATH to my ``.zshrc`` but I just wanted more. I found
`virtualenv <http://www.virtualenv.org/>`_ very useful with Python developmen and I
wanted to use it with Go. And
`virtualenvwrapper <http://www.doughellmann.com/projects/virtualenvwrapper/>`_
I use to manange all my virtual environments just made it easier to use.

First, create the Go virtual environment by:

.. sourcecode:: console

  $ mkvirtualenv go

Then edit the ``postactivate`` file in the virtual environment bin directory. Add in:

.. sourcecode:: bash

  export GOPATH=$VIRTUAL_ENV

Add edit ``postdeactivate`` file. Add in:

.. sourcecode:: bash

  unset GOPATH

That's it. When I wanted to work on Go, I just use ``workon go`` to switch to the virtual
environment and the $GOPATH will automatically set to the virtual environment. The ``pkg``
folder will hold all compiles libraries. The ``src`` folder will contain all the source code
and that's where I should put my source code.

For instance I wanted to write a library called mylib and a application called myapp, and
myapp will use mylib as a 3rd party package, I'll make two folders called mylib and myapp
in ``src`` folder and write code in corresponding folders. When I use ``import mylib`` in
myapp, Go will link both of them together.

Of course I could create more virtual environments for different Go projects and use
``workon projectname`` to switch from them. But as I'm just doing some simple stuff, one
single Go environment is already enough for me.

One thing to add, since mylib and myapp are in different folders, I could easily setup
git to track each of them. That's much convenient than a single of directory holds everything.
I find this writing code in different packages and linking them all together approach
really made the code easy to read, maintain and reuse when I use Python. And I'm quite
satisfied with what Go provides.

Now it's time to write some Go code.
