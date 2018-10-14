# Ubuntu安装tlp减少发热量，增加续航时间

`sudo add-apt-repository ppa:linrunner/tlp`

`sudo apt-get update`

`sudo apt-get install tlp-rdw`

`sudo apt-get install tp-smapi-dkms acpi-call-dkms`

启动TLP

`sudo tlp start`

当时我就执行了第3,4,5步