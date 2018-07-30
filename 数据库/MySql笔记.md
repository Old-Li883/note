# MySQL笔记

# 链接MySQL

mysql -u root -p

## 启动MySQL服务

service mysqld start;

## 停止MySQL服务

service mysqld stop

## 重启MySQL服务

service mysqld restart

## 添加用户

mysql>create user'(username)'@'host(主机IP)' identified by'(密码)';

**注：在命令行下MySQL结尾都要有分号**

**注：命令行下MySQL不分大小写**

## 常用管理命令

### 数据库

mysql>create database 数据库名;#创建数据库

mysql>show databases;#显示服务器中的数据库

mysql>use (数据库名);#选择需要操作的数据库

mysql>drop database 数据库名;#删除数据库

### 数据表

mysql>create table 表名(列名 类型,……);

mysql>show tables;#显示数据库的所有表

mysql>show columns from (数据表名);#显示数据表的属性等相关信息

mysql>show index from (数据表名)(\G);#显示数据表详细索引信息,\G是表示按列输出

mysql>insert into 表名(列名(一个个罗列)) values(值,一个个对应);#插入数据

mysql>drop table 表名;#删除表

mysql>select column_name.. from table_name '[where ...]'[limit n]''[offset m]';

**注**：

* where column_name 关系符 怎么样什么（例：select  * from test1 where age=3||where name regexp '(正则匹配式)'#后面这一个表示找出name中含有相关正则匹配的数据)
* like用法:where field1 like .... filed2(怎么怎么样) (例：where column_name like '%.com')#找出以.com结尾的东西
* union放在两个select后面并合并找出来的重复的数据
* oreder by  field1(那个地方) asc/desc#asc升序，desc降序

mysql>select * from 表名;#查看表中所有数据(如果有具体的列名就只输出这一列的数据)

mysql>update table_name set field1=new_value1,field2=new_value2 '[where]';#更新数据

mysql>delete from table_name [where ];#删除数据

mysql>select * from 表名 into outfile '文件路径加文件名';#导出表

mysql>load data local inrifle '文件名' into table 表名;#从文件导入表

mysql>alter table table_name drop(add) column_name;删除(增加)字段

mysql>alter table table_name modify column_name new_type修改字段类型

mysql>alter table table_name change old_column_name new_table_name new_type修改字段名称及类型 

## MySQL支持的数据类型

支持的数据类型分三类：

1. 数值：

   ​

   [![image](https://www.linuxdaxue.com/wp-content/uploads/2016/09/image_thumb-1.png)](https://www.linuxdaxue.com/wp-content/uploads/2016/09/image-1.png)

2. 时间：

   下面的表显示了需要的每个整数类型的存储和范围。

   [![image](https://www.linuxdaxue.com/wp-content/uploads/2016/09/image_thumb-1.png)](https://www.linuxdaxue.com/wp-content/uploads/2016/09/image-1.png)

3. 字符串：

   ![image](https://www.linuxdaxue.com/wp-content/uploads/2016/09/image_thumb-3.png)

（图片来自于Linux大学）

## 用户管理

create ueser'username'@'host' identified by '(密码)';#创建用户

grant privileges on databasename.tablename to 'username'@'host'#用户授权

revoke privilege on databasename.tablename from 'username'@'host';#撤销用户授权

set password for 'username'@'host' = password('newpassword');#修改密码

flush privileges;#刷新数据库，使新建用户生效

## 事物与回滚

每一个或一组特定的sql称为一种事物

回滚：回滚到这个事物最开始还没执行的情况

## 游标

一块内存，用于暂时存放受SQL语句影响到的数据

## Linux链接

https://www.linuxdaxue.com