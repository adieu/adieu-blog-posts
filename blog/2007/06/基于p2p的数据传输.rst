:title: 基于P2P的数据传输
:slug: 基于p2p的数据传输
:url: http://www.adieu.me/blog/2007/06/基于p2p的数据传输/
:published_on: 2007-06-10 02:38:24.000006

Joost在播放影片的时候，程序会把你的电脑做为Peer利用你的剩余带宽进行一定的数据传输工作。正是由于这种P2P的传输方式，Joost才能够完成流畅播放影片的目的。

有些时候会想，有没有可能将P2P的数据传输方式抽象出来，成为独立的package，大家可以基于这个统一的P2P引擎，来搭建自己的应用。

可以想到的应用有：

1. 网络在线点播。可以点播视频，音频，电影电视等。
2. 基于P2P的点对点文件传输。将原来的点对点直接传输改为通过很多的peer传输的方式，寻找最快路径。
3. BT下载。和现在的类似。
4. 反GFW系统。类似tor，通过其他的peer去访问网络。

其他当然还有很多可能性，希望能够看到类似产品的出现。