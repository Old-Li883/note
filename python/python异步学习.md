# python异步学习

协程

yield，不仅可以返回一个值，还可以接受参数

next(arg)，函数.send(arg)调用arg可选

## asyncio包

@asyncio.coroutine装饰器

把一个生成器标记为coroutine类型，然后把他扔到EventLoop中进行

例

```
import threading
import asyncio

@asyncio.coroutine
def hello():
    print('Hello world! (%s)' % threading.currentThread())
    yield from asyncio.sleep(1)
    print('Hello again! (%s)' % threading.currentThread())

loop = asyncio.get_event_loop()
tasks = [hello(), hello()]
loop.run_until_complete(asyncio.wait(tasks))
loop.close()
```

当调用第一个hello的时候，执行到`yield from asyncio.sleep(1)`主进程不会管这么多，而是继续往下执行第二个hello等到asyncio执行完返回值的时候才继续执行第一个hello后面的内容

## Python3.5中新语法

1. 把`@asyncio.coroutine`替换为`async`；
2. 把`yield from`替换为`await`。