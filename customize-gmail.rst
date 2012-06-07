:title: 自定义Gmail
:slug: customize-gmail
:url: http://www.adieu.me/blog/2007/03/customize-gmail/
:published_on: 2007-03-12 01:58:16

自从开始写blog之后就在考虑推广的问题。虽然写的时间还不长，但能够有更多的读者来关注自己的文字显然是一件很棒的事情。我不是一个高调的人，会把自己写的文章到处去张贴，但是我确实希望更多的人能够阅读我的东西。这些文字虽然文笔很差，但是其中包含了我思维的成果，细细品来还是能带给人一些思考。

从目前来看，我的读者来源可能有以下几个方面：

- 等待搜索引擎的收录，当有人在搜索时可能会点进来。
- 来自 `蚂蚁社区 <http://www.maayee.com/>`_ 的朋友。蚂蚁社区的blog导入功能对我这种融入感很差的人来说是个很贴心的设计，谢谢。
- 可能还有几个朋友，在我的强烈推荐之下会来看看。

来源貌似少的可怜，不过推广本身就是一件很需要耐心的工作。我相信只要写的东西能给人带来价值自然会有人会喜欢。

今天突发奇想，有了一个好玩的idea：我可以在email中推广我的blog。

如果只是简单的把自己的blog地址放在签名里面，等待有兴趣的人来点的话，就太普通了。我打算直接把最近的文章标题直接包含在email中，直接把我的blog更新推送给email的收件人，也许对方就会被标题所吸引。Further  more，整个过程自动化程度越高越好。

Gmail+Firefox+Greasemonkey的解决方案完美的满足了我的需求。

目前我已经使用了 Gmail Tweaks: Multiple  Signatures，它让我可以在Gmail发信时在多个签名中切换。我只需要在现有的脚本上加以改造，让脚本动态的去我的blog上抓取最新的Posts就可以了。

整个过程还是遇到了一些问题，不过最后的结果让我非常满意。如果你也使用Greasemonkey的话，脚本在 `这里`__ 。另外还需要在服务器  端写一段小程序来生成脚本，这个每个人可能遇到的情况不同，就不放出来了。

最近喜欢用Greasemonkey写一些小脚本，为了增加蚂蚁的阅读效果，写了一段脚本来处理ul和ol标签，脚本在 `这里`__ 。

时间不早了，先写到这里吧，明天争取整理一下今天写脚本中积累的经验。

附个效果图：

.. image:: http://farm1.static.flickr.com/158/417729573_97f9d7f8d2_o.jpg

__ http://www.adieu.cn/src/gmail/gmailtweaksmultiplesigna.user.js
__ http://www.adieu.cn/src/maayee/maayeeoptimized.user.js
