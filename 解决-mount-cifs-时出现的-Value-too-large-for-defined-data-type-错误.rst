.. url: http://www.adieu.me/blog/2010/11/解决-mount-cifs-时出现的-Value-too-large-for-defined-data-type-错误/
.. published_on: 2010-11-17 15:23:12

解决 mount cifs 时出现的 Value too large for defined data type 错误
===========================================================================

今天遇到的一个问题，记录一下，以便日后备查。

今天在捣鼓openwrt时，打算挂载局域网内的一个samba share，在成功挂载后执行 ls 时报错:

.. sourcecode:: console

  root@OpenWrt:/mnt/cifs# ls
  ls: can't open '/mnt/cifs': Value too large for defined data type

经过一段不短的时间调试以及搜索后，总算找到了解决方案，参见 `这里 <https://wiki.archlinux.org/index.php/Samba#Error:_Value_too_large_for_defined_data_type>`_ 

使用以下指令挂载samba share后，问题解决:

.. sourcecode:: console

  root@OpenWrt:~# mount.cifs //IP/SHARE /mnt/cifs -o nounix,noserverino

Update:
  貌似这个问题很早就有了，参见 `这里的讨论 <https://bugs.launchpad.net/archlinux/+source/samba/+bug/406466>`_: 