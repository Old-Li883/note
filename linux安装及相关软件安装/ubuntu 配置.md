# ubuntu 配置

## 清理系统

`sudo apt-get remove ...`

unity-webapps-common //Amazon链接

libreOffice-common

.......

## 系统美化工具

`sudo apt-get install unity-tweak-tool`

`sudo apt-get install gnome-tweak-tool`

终端打开

`gnome-tweaks`

我的图标类型下载

```
sudo add-apt-repository ppa:snwh/pulp
sudo apt-get update
sudo apt-get install paper-icon-theme
```

## uGet与aria2安装

类似于迅雷的下载插件

uGet安装

```
sudo add-apt-repository ppa:plushuang-tw/uget-stable
sudo apt-get update
sudo apt-get install uget
```

aria2安装

```
sudo add-apt-repository ppa:t-tujikawa/ppa
sudo apt-get update
sudo apt-get install aria2
```

配置uGet默认下载插件为aria2
进入edit->settings->Plug-in

第一行选择aria2

4、设置uGet为Chrome的默认下载插件

安装uget-chrome-wrapper

```
sudo add-apt-repository ppa:slgobinath/uget-chrome-wrapper
sudo apt update
sudo apt install uget-chrome-wrapper
```

chrome插件uGet Integration

这样就可以不用google下载了

## 安装shutter

```
sudo apt-get install shutter
```

添加快捷键

Settings->Keyboard

Command:`shutter -s`