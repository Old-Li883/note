# ubuntu 配置桌面文件（eclipse为例）

创建一个.desktop文件

修改权限为可执行程序

进行配置

[Desktop Entry]
version=1.0
Type=Application
Name[ro]=eclipse.desktop
Comment[aa]=Ubuntu
URL=file:///opt/eclipse/eclipse
Icon=file:///opt/eclipse/icon.xpm
X-Ubuntu-Gettext-Domain=nihao

or？

[Desktop Entry]
version=1.0
Type=Application
Name[ro]=eclipse.desktop
Comment[aa]=Ubuntu
URL=opt/eclipse/eclipse`可执行文件`
Icon=/opt/eclipse/icon.xpm`图标`
Terminal=false`启动时不打开终端`

StartupNotify=false

Categories=Application;Development;
如果打不开，右键属性在命令那行自己输入可执行文件地址











































































































