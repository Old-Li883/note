# ubuntu软件商店提示has install-snap change in progress问题

## 问题背景

在ubuntu软件商店安装软件时忽然报错：

`cannot install “chromium”: snap “chromium” has “install-snap” change in progress`

`cannot install “electronic-wechat”: snap “electronic-wechat” has “install-snap” change in progress`

## 解决方案

1. 输入`snap changes`找到status为doing的ID
2. 在`sudo snap abort ID`即可