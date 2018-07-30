# Session、cookie学习

## 什么是Session

由于http是无状态的，Session的存在更好的识别两个有关联的请求。session存在与一次浏览器与服务器的交互中，当页面关掉Session会消失，再次打开页面时，Session会重新分配（如果只是刷新页面则不会重新分配）。session一般储存在文件中，可以在cookie找到相关的session_id从而访问到相关的文件。session储存在服务器。

## 什么是cookie

cookie是有web服务器创建储存在用户本地硬盘上的一些关于用户的资料。当用户访问文本服务器时，浏览器会检查本地的Cookie，并将其原样发送给服务器。

## 二者区别

1. cookie存在浏览器上，session存放在服务器上
2. cookie不是很安全（cookie欺骗），session相对安全
3. session会在一定时间内保存在服务器上，当当访问量增多，会比较占用服务器性能。如果考虑性能应用cookie