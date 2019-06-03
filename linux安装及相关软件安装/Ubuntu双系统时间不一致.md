# Ubuntu双系统时间不一致

将硬件时间UTC改为CST，双系统时间保持一致。

`sudo timedatectl set-local-rtc 1`

先在ubuntu下更新一下时间，确保时间无误：

`sudo apt-get install ntpdate`

`sudo ntpdate time.windows.com`

然后将时间更新到硬件上：
`sudo hwclock --localtime --systohc`