# vscode c++安装并使用

## 先安装插件

c/c++,c/c++ Clang Command Adapter

## 再写一个cpp文件

按f5会生成一个launch.json文件

修改地方用下面用`//`标注

配置文件

>{
>
>​    // 使用 IntelliSense 了解相关属性。
>
>​    // 悬停以查看现有属性的描述。
>
>​    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
>
>​    "version": "0.2.0",
>
>​    "configurations": [
>
>​        {
>
>​            "name": "(gdb) Launch",
>
>​            "type": "cppdbg",
>
>​            "request": "launch",
>
>​            "program": "${workspaceFolder}/a.out",//这个地方改成这样
>
>​            "args": [],
>
>​            "stopAtEntry": false,
>
>​            "cwd": "${workspaceFolder}",//这个地方改成这样
>
>​            "environment": [],
>
>​            "externalConsole": true,
>
>​            "MIMode": "gdb",
>
>​            "setupCommands": [
>
>​                {
>
>​                    "description": "Enable pretty-printing for gdb",
>
>​                    "text": "-enable-pretty-printing",
>
>​                    "ignoreFailures": true
>
>​                }
>
>​            ]
>
>​        }
>
>​    ]
>
>}

## 再配置task.json

按Ctrl+p打开命令面板，输入>task，选择others，会生成一个task.json文件,内容如下

> {
>
> ​    "version": "0.1.0",
>
> ​    "command": "g++",
>
> ​    "isShellCommand": true,
>
> ​    "args": [
>
> ​        "-g",
>
> ​        "${workspaceRoot}/文件名字"
>
> ​    ],
>
> ​    "showOutput": "always"
>
> }

其实真正修改的也就只有command项和args项，command就是调用的控制台命令（就是我们平常用控制台编译时输入的命令），然后args就是命令行参数了，-g参数是必须的，否则到时候没有调试信息，vscode会无法设置断点。

## 编译运行

Ctrl+shift+b编译,一定要记得编译!!!否则无法运行,加断点

就会在终端输出

## 注意

一个c程序一个文件夹,一个配置,和在vs下一样