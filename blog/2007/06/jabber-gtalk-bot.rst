:title: Jabber Gtalk Bot初体验
:slug: jabber-gtalk-bot
:url: http://www.adieu.me/blog/2007/06/jabber-gtalk-bot/
:published_on: 2007-06-03 22:57:12.000006

Jabber已经越来越有影响力了，心血来潮今天想研究下Jabber Bot怎么写。

1. 首先安装Jabber的Python封装 `xmpppy <http://xmpppy.sourceforge.net/>`_
2. xmpppy需要调用dns包，安装 `pydns <http://xmpppy.sourceforge.net/>`_
3. 写一段代码，保存为xsend.py

  .. sourcecode:: python

    import sys,os,xmpp

    if len(sys.argv) > 2:
      print "Syntax: xsend JID text"
      sys.exit(0)

    tojid=sys.argv[1]
    text=' '.join(sys.argv[2:])

    jidparams={}

    jidparams['jid']='yourname@gmail.com'
    jidparams['password']='yourpassword'

    jid = xmpp.protocol.JID(jidparams['jid'])
    cl = xmpp.Client(jid.getDomain(),debug=[])
    cl.connect(('talk.google.com',5222))
    cl.auth(jid.getNode(),jidparams['password'])

    cl.send(xmpp.protocol.Message(tojid,text,typ='chat'))

4. 用xsend.py targetname@gmail.com text的语法发送消息
5. 没有第五步了，不过记得要把发信息的gmail帐号和收信息的gmail帐号加为好友才发的过去哦。

有时间可以自己写个bot来玩玩。也许每人都有自己定制bot的时代已经离我们不远了。
