# MySQL学习

## 用户登录

`mysql -u -root -p`用root登录

可以在`user`下注册普通用户，并设置权限

## 表的创建

`AUTO_INCREMENT`定义主键自增

`PRIMARY_KEY`定义主键自增

## MySQL事物

### 四个条件

原子性：全部执行，全部不执行。发生错误回滚。

一致性：数据库完整性没有被破坏

隔离性：对多个事物进行读写和修改能力

持久性：修改是永久的

### 相关操作

MySQL默认是自动提交的

BEGINH或STARTTRANSACTINO显示地开启一个事物

COMMIT （WORK）

ROLLBACK （WORK）：撤销正在进行的所有未提交的修改

SAVEPOINT identifier：创建一个保存点，一个事物中可以有多个保存点

RELEASE SAVEPOINT identifier：删除一个事物的保存点

ROLLBACK TO identifer：把事务回滚到标记点

SET TRANSACTION：设置事务隔离级别

SET AUTOCOMMIT=0禁止自动提交；1开启自动提交

