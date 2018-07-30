# Ubuntu网络解决方法

1. `rfkill list all`#查看网络情况
2. `rfkill unblock all`#解决soft block问题
3. `sudo modprobe -r ideapad_laptop`#解决hard block问题