# pymysql学习

## 链接数据库

pymysql.connect('localhost','user','db','password')

## 创建游标对象

db.cursor()

## 执行语句

cursor.execute()

## 获取数据

cursor.fetchone()（获取单条数据）一个格格？

cursor.fetchall()（获取所有数据）

## 插入操作

try: 

执行sql语句

​	cursor.execute(sql) 

提交到数据库执行 

​	db.commit() 

except: 

​	 如果发生错误则回滚 

​	db.rollback()

