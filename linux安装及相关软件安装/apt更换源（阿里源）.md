# apt更换源（阿里源）

1. 在/etc/apt/sources.list文件下修改，修改前先做好备份
2. 将阿里源复制进去
3. 执行sudo apt-get update
4. 执行sudo apt-get upgrade
5. 阿里源

deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse 

deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse 

deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse 

deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse 

deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse 

deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse 

deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse 

deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse