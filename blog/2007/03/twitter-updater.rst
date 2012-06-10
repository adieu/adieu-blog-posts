:title: Twitter Updater
:slug: twitter-updater
:url: http://www.adieu.me/blog/2007/03/twitter-updater/
:published_on: 2007-03-27 01:54:14.000001

`Twitter <http://www.twitter.com/>`_ 是一个蛮好玩的服务。它所倡导的随时随地记录自己状态的生活方式可能会成为博客的一种新的模式。

但是Twitter本身提供的三种更新方式却很难让我满意。Web速度太慢，IM好像坏掉了，Phone应该在中国还使用不了。

好在Twitter提供了开放的API，可以让程序员们自由发挥。今天花了半天的时间做了个Twitter  Updater，让我可以使用email更新Twitter。它的原理如下：

- 当我要更新时就发送email到一个我预先设定的email地址
- 服务器上有一个小程序会定期检查这个邮箱
- 如果有新邮件则判断是否是有效用户发来的
- 如果是有效用户则将正文更新到Twitter

这个小程序让我不论是否在上网，都可以随时随地的写email更新我的Twitter状态。真正实现了随时随地记录自己生活的目标。

其实这个小程序应该作为Weenkend Project来做，其中有不少代码之前都没接触过。之后如果有时间的话我会整理一下今天的过程，还是有蛮多心得的。

因为更新Twitter需要用户名和密码，所以帮大家提供服务有点麻烦。

代码现在还比较丑陋，在整理好之前就先不发布了。如果需要源代码，请给我Email。