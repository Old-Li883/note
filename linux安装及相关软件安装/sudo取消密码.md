sudo取消密码

sudo gedit /etc/sudoers

！！！找到
%admin ALL=(ALL) ALL
注释之， 在下面加上

%admin ALL=(ALL) NOPASSWD: ALL
