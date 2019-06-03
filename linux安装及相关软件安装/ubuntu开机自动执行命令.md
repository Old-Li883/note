# ubuntu开机自动执行命令

## 设置开机自启动

Ubuntu18.04 不再使用initd管理系统，改用systemd.

然而systemd很难用，改变太大，跟之前的完全不同。

使用systemd设置开机启动
为了像以前一样，在/etc/rc.local中设置开机启动程序，需要以下几步：

将 /lib/systemd/system/rc-local.service 链接到 /etc/systemd/system/ 目录下面来：
`sudo ln -fs /lib/systemd/system/rc-local.service /etc/systemd/system/rc-local.service`

创建/etc/rc.local文件
`sudo touch /etc/rc.local `

赋可执行权限
`sudo chmod 755 /etc/rc.local `

编辑rc.local，添加需要开机启动的任务
`sudo gedit /etc/rc.local`

接下来在rc.local中写一个脚本文件就行

例：

```shell
#!/bin/zsh
sudo modprobe -r ideapad_laptop
```

