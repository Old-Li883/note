# ubuntu tcpdump使用

1.网上下载获得libpcap和tcpdump

     http://www.tcpdump.org/

 2.安装c编译所需包：apt-get install build-essential

 3.安装 libpcap的前置：apt-get install flex,apt-get install bison

 4.安装libpcap。

    tcpdump的使用必须有这库。

    tar  xvfz libpcap-1.2.1.tar.gz     //解压

   进入解压之后的文件目录   运行./configure      //生成makefile文件

* 文件可能会执行不了这时候可能有些东西没有安装我这次使用`sudo apt-get install -y byacc`解决了

   make              //进行编译

   make install   //安装   库文件默认安装在目录  /usr/lib,头文件默认安装在  /usr/include

3.安装tcpdump

    tar  xvfz tcpdump.4.2.1.tar.gz     //解压

   进入解压之后的文件目录   运行./configure      //生成makefile文件

   make              //进行编译

   make install   //安装   库文件默认安装在目录  /usr/lib,头文件默认安装在  /usr/include



测试是否成功安装：命令行输入 tcpdump有网络信息显示！！



可能遇到的问题：

    1.#tcpdump

       \#tcpdump: no suitable device found

       原因：网络监听需要root权限，切换到root用户下就可以正常使用了