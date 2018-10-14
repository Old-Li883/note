# tcpdump学习

更多内容请参看`man tcpdump`

## 选项

- `-n` 表示不要解析域名，直接显示 ip。
- `-nn` 不要解析域名和端口
- `-X` 同时用 hex 和 ascii 显示报文的内容。
- `-XX` 同 `-X`，但同时显示以太网头部。
- `-S` 显示绝对的序列号（sequence number），而不是相对编号。
- `-i any` 监听所有的网卡
- `-v, -vv, -vvv`：显示更多的详细信息
- `-c number`: 截取 number 个报文，然后结束
- `-A`： 只使用 ascii 打印报文的全部数据，不要和 `-X` 一起使用。截取 http 请求的时候可以用 `sudo tcpdump -nSA port 80`！

## 简单使用

#### 1. tcpdump -nS

监听所有端口，直接显示 ip 地址。

#### 2. tcpdump -nnvvS

显示更详细的数据报文，包括 tos, ttl, checksum 等。

#### 3. tcpdump -nnvvXS

显示数据报的全部数据信息，用 hex 和 ascii 两列对比输出。

下面是抓取 ping 命令的请求和返回的两个报文，可以看到全部的数据。

## 过滤器

过滤器也可以简单地分为三类：`type`, `dir` 和 `proto`。

`Type` 让你区分报文的类型，主要由 `host`（主机）, `net`（网络） 和 `port`（端口） 组成。`src` 和 `dst` 也可以用来过滤报文的源地址和目的地址。

#### host: 过滤某个主机的数据报文

```
tcpdump host 1.2.3.4
```

#### src, dst: 过滤源地址和目的地址

```
tcpdump src 2.3.4.5
tcpdump dst 3.4.5.6
```

#### net: 过滤某个网段的数据，[CIDR](http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) 模式

```
tcpdump net 1.2.3.0/24
```

#### proto: 过滤某个协议的数据，支持 tcp, udp 和 icmp。使用的时候可以省略 proto 关键字。

```
tcpdump icmp
```

#### port: 过滤通过某个端口的数据报

```
tcpdump port 3389
```

#### src/dst, port, protocol: 结合三者

```
tcpdump src port 1025 and tcp
tcpdump udp and src port 53
```

此外还有指定端口和数据报文范围的过滤器：

#### port 范围

```
tcpdump portrange 21-23
```

#### 数据报大小，单位是字节

```
tcpdump less 32
tcpdump greater 128
tcpdump > 32
tcpdump <= 128
```

还有`and，&&`，`or，||`，`not，!`等逻辑关系

## 输出到文件

使用 tcpdump 截取数据报文的时候，默认会打印到屏幕的默认输出，你会看到按照顺序和格式，很多的数据一行行快速闪过，根本来不及看清楚所有的内容。不过，tcpdump 提供了把截取的数据保存到文件的功能，以便后面使用其他图形工具（比如 wireshark，Snort）来分析。

`-w` 选项用来把数据报文输出到文件，比如下面的命令就是把所有 80 端口的数据导入到文件

```
# sudo tcpdump -w capture_file.pcap port 80
```

`-r` 可以读取文件里的数据报文，显示到屏幕上。

```
# tcpdump -nXr capture_file.pcap host web30
```

**NOTE：保存到文件的数据不是屏幕上看到的文件信息，而是包含了额外信息的固定格式 pcap，需要特殊的软件来查看，使用 vim 或者 cat 命令会出现乱码。**

## 理解tcpdump的输出

截取数据只是第一步，第二步就是理解这些数据，下面就解释一下 tcpdump 命令输出各部分的意义。

```
21:27:06.995846 IP (tos 0x0, ttl 64, id 45646, offset 0, flags [DF], proto TCP (6), length 64)
    192.168.1.106.56166 > 124.192.132.54.80: Flags [S], cksum 0xa730 (correct), seq 992042666, win 65535, options [mss 1460,nop,wscale 4,nop,nop,TS val 663433143 ecr 0,sackOK,eol], length 0

21:27:07.030487 IP (tos 0x0, ttl 51, id 0, offset 0, flags [DF], proto TCP (6), length 44)
    124.192.132.54.80 > 192.168.1.106.56166: Flags [S.], cksum 0xedc0 (correct), seq 2147006684, ack 992042667, win 14600, options [mss 1440], length 0

21:27:07.030527 IP (tos 0x0, ttl 64, id 59119, offset 0, flags [DF], proto TCP (6), length 40)
    192.168.1.106.56166 > 124.192.132.54.80: Flags [.], cksum 0x3e72 (correct), ack 2147006685, win 65535, length 0
```

最基本也是最重要的信息就是数据报的源地址/端口和目的地址/端口，上面的例子第一条数据报中，源地址 ip 是 `192.168.1.106`，源端口是 `56166`，目的地址是 `124.192.132.54`，目的端口是 `80`。 `>` 符号代表数据的方向。

此外，上面的三条数据还是 tcp 协议的三次握手过程，第一条就是 `SYN` 报文，这个可以通过 `Flags [S]` 看出。下面是常见的 TCP 报文的 Flags:

- `[S]`： SYN（开始连接）
- `[.]`: 没有 Flag
- `[P]`: PSH（推送数据）
- `[F]`: FIN （结束连接）
- `[R]`: RST（重置连接）

而第二条数据的 `[S.]` 表示 `SYN-ACK`，就是 `SYN` 报文的应答报文。