---
title: Replit免费服务器搭建超高速节点
date: 2023.1.2
tags:
- 翻墙
- vpn
- replit
categories:
- 翻墙
- 搭建节点
---
# Replit免费服务器搭建超高速节点

Replit（https://repl.it）是一个基于浏览器的云端协同开发平台，可用于构建开发环境、实时协作、托管网络应用等。Replit提供可创建动态或者静态网站的容器，并会自动生成免费https域名（格式为：项目名.用户名.repl.co）。这代表着任何人都可以试用Replit的云服务器创建自己的网站，或者是其他的服务，例如v2ray，而且这一切，都是免费的。

Replit官方文档：https://docs.replit.com/

注册
注册地址 https://repl.it
可选谷歌账号、苹果账号、fb或者GitHub账号一键登录，或者自己用邮箱注册也行，邮箱注册的需要收信验证一下。

其他的没什么说的，就是跳过，或者随便选择吧；

Replit测试
注册后，我随便弄了个Repl，经测试Repl项目是在谷歌云中运行的，主服务器8核64G，当然了这不可能都给你用，所有Repl项目会共用这台服务器，直到它到了负荷，会自动切换到下一台。

随便开一个Repl，然后shell进入，查看当前主机状态，负载蛮高的。
截屏2022-12-17 14.29.06.png

每个免费的项目会得到0.2-0.5个CPU512M内存1GB的硬盘空间，想提高性能就要充值！

另外就是replit.nix，需要自己集成；最后，Replit的项目就叫：repl；

创建repl
静态或动态网站
在home中，点击Create，然后选择HTML, CSS, JS（静态），PHP Web Server(动态)，然后Create Repl即可。

倘若网站的文件比较少，可以直接写代码，如果文件比较多用git之前先要把Replit连接到你的github。

Replit虽然也提供了数据库，我看仅仅适合学习用途，动态网站所需的数据库还是自己找个免费的，例如：https://freedb.tech/

简单说，就是我们的内容托管在Replit，数据库还是需要用别人的，想尝试Replit自己的SQLite服务，也可以试试。

可能是我测试的时间比较短，并没有发现问题。Replit官方说：永远在线服务是要购买的，这说明，这个空间并不能永久在线！做站就要认真考虑一下了。

为自己的网站绑定域名
在网站页面，点击Domain Linking，输入自己的域名，按照提示修改A记录或者使用CNAME，再添加TXT记录，然后检查通过即可绑定域名访问。

创建其他repl
这里没什么可说的，Python、C#、node.js、Java都可以随便尝试。

共享自己的项目
在自己repl的右上角，点击Invite即可给项目生成一个URL，发给你的伙伴即可实现共享。

其他功能
Replit的其他功能都可以在文档中找到，够玩好几天了。

搭建v2ray
我从今天才开始了解Replit，感谢热心网友提供的搭建方法。

1、浏览器登录自己的Replit账号，新窗口打开https://replit.com/@wanghanzhe/V2RAY?v=1
备用地址： https://replit.com/@oracleservice/V2RAY

2、fork这个项目，仅需点击Use Template，然后给项目取个名字，然后Use Template就行了。

3、点击run，Console会输出password和url，直接添加到app中即可使用；

截屏2022-12-17 15.50.26.png

4、速度如何呀？ 谷歌的服务器不用问，电脑上我都没测试，直接告诉你能跑满，而且现在用的人也不太多，白嫖党作为自己的主力线路好像也没压力。

5、个别伙伴扫描二维码不能直接导入v2客户端，请参考如下配置：
photo_2022-12-17_20-55-12.jpg

搭建trojan，感谢热心网友提供的代码
非常简单，Fork https://replit.com/@sos801107/trojan?v=1
备用地址： https://replit.com/@oracleservice/trojan
然后运行 bash main.sh
即可看到 trojan链接和二维码，实测路由器可用。
补充
另外就是有伙伴客户端不支持，咱的环境都不一样，我没法一个一个测试，大家参考一下已经成功的伙伴：
1、这个节点放在手机matsuri可以使用；
2、手机小火箭完全支持，可以直接识别url自动添加；
3、电脑端可以用shadowsocks客户端+v2ray-plugin插件使用；
4、這是ss+v2ray-plugin 客戶端若選v2ray設置是連不了的；
5、用来打绝地求生延迟低，不卡；
也是今天上午测试的，我本地是移动100M网络，fast测速45M，延迟80ms。
Replit获得root权限的方法
首先，我们在Replit创建一个Bash；
然后我们在项目右侧Console窗口依次执行下列命令
wget https://cdn.discordapp.com/attachments/853535040250970113/878590395611775016/yt.zip （需要回车一次）
unzip yt.zip （需要回车一次）
unzip root.zip
tar -xvf root.tar.xz
./dist/proot -S . /bin/bash
以上的命令说明：首先下载yt.zip，然后解压文件，恢复文件，然后执行bash；

当我们执行完所有命令，你就会发现，已经是root啦～
获取了root权限，可玩性高多了！！
视频教程：
https://www.bilibili.com/video/BV1C8411p7xo/
https://www.youtube.com/watch?v=ZsQ6NEZeei0
https://www.youtube.com/watch?v=t2jhaZMvWCE

参考资料：
https://zhuanlan.zhihu.com/p/521214589
https://github.com/techcode1001/replit_root
感谢热心网友提供的资源和信息！