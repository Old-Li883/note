# ubuntu vscode Java安装

## jdk安装

# Ubuntu 搭建JAVA开发环境

## 下载JDK

[Oracle官网下载](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

## 安装

- 创建Java目录

  ```
  sudo mkdir /usr/local/java
  ```

- 解压文件并移到Java目录

  ```
  tar zxvf jdk-8u152-linux-64x.tar.gz
  sudo mv jdk1.8.0_152/ /usr/local/java/
  ```

## 配置环境变量

打开profie文件

```
sudo vi /etc/profile
```

将以下代码复制到profile文件

```
#JAVA_HOME
export JAVA_HOME=/usr/local/java/jdk1.8.0_152
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:${JRE_HOME}:$PATH
```

执行`source /etc/profile`命令

## 完成安装

输入 `java -version`
控制台输出

```
java version "1.8.0_152"
Java(TM) SE Runtime Environment (build 1.8.0_152-b16)
Java HotSpot(TM) 64-Bit Server VM (build 25.152-b16, mixed mode)

```

## vscode配置

1. Language support for Java ™ for Visual Studio Code
2. Java Extension Pack
3. Debugger for Java
4. Java Test Runner

## 运行

按下f5出来launch.json

选择添加配置，然后直接点添加配置中java launch program 返回去运行就行了