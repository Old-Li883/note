# ubuntu 解决网络经常掉线

`sudo gedit /etc/ppp/options`

```shell
lcp-echo-failure 4
lcp-echo-interval 30 
把lcp-echo-failure 4改为lcp-echo-failure 15
```



