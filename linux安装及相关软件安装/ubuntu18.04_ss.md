# 科学上网笔记

环境ubuntu18

## 1.安装ss-qt5

在低版本的ubuntu中

sudo add-apt-repository ppa:hzwhuang/ss-qt5

sudo apt-get update

sudo apt-get install shadowsocks-qt5 

这样就行了

但在18里很不幸

因为在ppa:hzwhuang/ss-qt5 并没有18.04版本的源，所以再执行update时会出现这个错误。 

你在做第二步时会报错

E: 仓库 “http://ppa.launchpad.net/hzwhuang/ss-qt5/ubuntu bionic Release”

解决方法

在你的/etc/apt/sources.list.d目录下，看 这个文件(hzwhuang-ubuntu-ss-qt5-bionic.list )将里面的bionic 改成xenial ,保存再运行 sudo apt-get update ,最后再运行一次 sudo apt-get install shadowsocks-qt5 就好了。

代理设置
设置proxy的代理协议为SOCKS5，代理服务器为127.0.0.1，端口为1080。这样应该就可以使用这个代理进行上网了

进一步还可以使用自动模式，规则列表设置选择AutoProxy 然后将【https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt】填进去，点击下面的立即更新情景模式，会有提示更新成功！
