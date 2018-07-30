# 第一个flask项目记录

## 文件夹的建立

project项目下建立/app,/tmp两个文件夹

project项目下建议config.py，run.py

app下建立/static（存储静态文件），/templates（存储模板）两个文件夹

app下建立`__init__.py`，models.py，views.py(打开网页时主页面显示)

## 第一个flask项目

`__init__.py文件`

> `from flask import Flask`
>
> `app=Flask(__name__)`
>
> import views

**注**:app 文件夹其实是一个python包，from app import views 这句话也就是从 包app里面导入 views模块.

`view.py`

> `from app import app`
>
> `@app.route('/')`
>
> `def index():`
>
> ​	`return 'hello world'`

`run.py`

> `from app import app`
>
> `if __name__=='main'`
>
> ​	`app.debug=True`
>
> ​	`app.run()`