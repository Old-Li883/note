# ubuntu 安装qq

Github主页(大家多多给这位大佬的项目加星): [https://github.com/askme765cs/Wine-QQ-TIM](https://link.jianshu.com/?t=https%3A%2F%2Fgithub.com%2Faskme765cs%2FWine-QQ-TIM)

下载随便一个qq版本，运行`install.sh`安装

安装wine

> `sudo dpkg --add-architecture i386 
> wget -nc https://dl.winehq.org/wine-builds/Release.key
> sudo apt-key add Release.key
> sudo apt-add-repository https://dl.winehq.org/wine-builds/ubuntu/
> sudo apt-get update
> sudo apt-get install --install-recommends winehq-stable`