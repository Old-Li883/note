# python 再学习

input输入的是str类型

str是不可变对象

tuple不可变但是可以改变tuple中的dict可变

mac/linux中

加入

```
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

第一行：这是一个可执行的python程序(windows下会忽略这个注释)

第二行：表示用UTF-8编码

dict的key对象是不可变的

set对象：只有key的集合，无重复元素，可以用它来做集合的交集并集之类的

Python返回多个值返回以tuple的形式返回

函数的参数形式，必须参数在前，默认参数在后，如果改变了默认参数的内容下次调用默认参数就会改变

`带*的参数是可变参数`就是传入的值可以使0,1，或多个，这些可变参数会自动组装成一个tuple，本身是一个list（tuple）`*`在前面修饰

关键字参数，允许你传入0个或多个含参数名参数，会在内部自动组装为一个dict

关键字参数在可变参数的后面，如果没有可变参数就必须加一个`*`来分隔，可以指定窜入关键字参数的参数名字

列表生成器（主要是迭代，在`[]`里写相关条件）（对象及简单对象方法可以做很多东西，加入循环，双重循环，判断条件）

生成器就是将列表生成器外的`[]`变成`()`

next得到下一个结果，不过一般用for循环

函数里面用yield

例

>```
>def fib(max):
>    n, a, b = 0, 0, 1
>    while n < max:
>        yield b
>        a, b = b, a + b
>        n = n + 1
>    return 'done'
>```
>
>```
>for n in fib(6):
>...     print(n)
>...
>1
>1
>2
>3
>5
>8
>```



但是用`for`循环调用generator时，发现拿不到generator的`return`语句的返回值。如果想要拿到返回值，必须捕获`StopIteration`错误，返回值包含在`StopIteration`的`value`中： 

>```
>>>> g = fib(6)
>>>> while True:
>...     try:
>...         x = next(g)
>...         print('g:', x)
>...     except StopIteration as e:
>...         print('Generator return value:', e.value)
>...         break
>...
>g: 1
>g: 1
>g: 2
>g: 3
>g: 5
>g: 8
>Generator return value: done
>```

## 迭代器

可以被`next()`函数调用并不断返回下一个值的对象称为迭代器：`Iterator`。

凡是可作用于`for`循环的对象都是`Iterable`类型；

凡是可作用于`next()`函数的对象都是`Iterator`类型，它们表示一个惰性计算的序列；

集合数据类型如`list`、`dict`、`str`等是`Iterable`但不是`Iterator`，不过可以通过`iter()`函数获得一个`Iterator`对象。

Python的`for`循环本质上就是通过不断调用`next()`函数实现的，例如：

```
for x in [1, 2, 3, 4, 5]:
    pass
```

实际上完全等价于：

```
# 首先获得Iterator对象:
it = iter([1, 2, 3, 4, 5])
# 循环:
while True:
    try:
        # 获得下一个值:
        x = next(it)
    except StopIteration:
        # 遇到StopIteration就退出循环
        break
```

## 返回函数

闭包：函数可以返回函数（双层函数，一般在调用时外内各调用一次），相关参数和变量都保存在返回的函数中

## 装饰器

在一个函数前后动态加入功能，本质上decorator就是一个返回函数的高阶函数

如果decorator要传入参数就要编写一个decorator的高级函数

@functools.wraps(func) 把原始函数的`__name__`等属性复制到wrapper()函数中

## 偏函数

固定某一函数的参数

## 类的迭代

`__iter__`与`__next__`然后就可以用for循环来对类进行迭代，每次都会执行一次`__next__`

`__getitem__`是一个可以用游标获取迭代对象的方法

## 错误调试

try......except.......finally

raise

## 单元测试

包unittest

继承unittest.TestCase

assertEqual等方法进行测试

setUp，tearDown

执行 unittest.main()

## 文档测试

## 文件读取

with open ... as ...:

方法read()，readline()，readlines()

write()

## 序列化

json序列化反序列化

关于类的序列化反序列化

## 进程与线程

开启进程`Process(target=函数名,args=(函数所需参数,))`

进程池，Pool，close，join

进程间的通信，包Queue，建立一个队列然后用一个一个开启进程可以向队列输入数据，输出数据

线程，包threading，threading.Thread(target=函数名,name=自己起线程名)

线程锁：加了之后一个函数只能由一个线程执行

Python中由GIL锁，多线程用不到多核，要想用到多核就必须用c语言来拓展，或者直接用多进程

分布式进程操作，包multiprocessing支持多进程

