# js笔记

变量要用var声明

## 字符串

多行字符串除了用\n还可以用反引号``

可以通过索引来找相应的字符

方法：

.length

.toUpperCase

.toLowerCase

.indexOf  //搜索指定字符串位置

.substring  //返回指定索引区间的子串

## 数组

一个数组里面可以是任意的数据类型，通过索引来查找

方法：

.indexOf

.slice //切片

.push //向尾添加若干元素

.pop

.unshift //向头部添加若干元素

.shift //弹出头部第一个元素

.sort // 排序

.reverse //翻转

.splice //从指定的索引开始删除若干元素，然后再从该位置添加若干元素

.concat //链接两个

.join //把.....加入......

## 对象

无序的集合数据类型，有若干个键值对组成

可以增加

delete 删除

## Map和Set

Map    键值对的结构

var m = new Map([[],[],[]])

.set

.has

.get

.delete

Set 键结构，但不储存value

var s1 = new Set([])

.add

delete

# iterable

for ..... of ......遍历

用forEach迭代

a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    console.log(element + ', index = ' + index);
});

a指向一个迭代对象

`Set`与`Array`类似，但`Set`没有索引，因此回调函数的前两个参数都是元素本身

## 函数

定义：function ....{

}

传入参数比定义函数多也没有问题

利用`arguments`，你可以获得调用者传入的所有参数。

rest

return 标准写法

变量声明会提升，但赋值不会提升

名字空间，为避免命名冲突，可以把名字放到一个空间中

可以用解构赋值，但对应的层级应该一样

方法中this指向问题

apply,call修改this指向

高阶函数： //参数是函数

map

reduce

filter //根据函数返回是true还是false来决定是否保留这个值

sort //通过返回1,1,0来自定义排序规则

闭包：

在闭包中可以存在私有变量

闭包中引用循环变量要再建一个闭包

箭头函数：匿名函数的简写，但也略有不同

generator：function*定义

yield

return结束

.next() //调用

## 标准格式

正则表达式的匹配

构建正则表达式对象

1. /  /
2. new RegExp('')  //要考虑字符转义

json序列化

JSON.stringify();

第二个参数可以加入输出指定的属性

反序列化：

JSON.parse()

## 面向对象编程

```
// 原型对象:
var Student = {
    name: 'Robot',
    height: 1.2,
    run: function () {
        console.log(this.name + ' is running...');
    }
};

function createStudent(name) {
    // 基于Student原型创建一个新对象:
    var s = Object.create(Student);
    // 初始化新对象:
    s.name = name;
    return s;
}

var xiaoming = createStudent('小明');
xiaoming.run(); // 小明 is running...
xiaoming.__proto__ === Student; // true
```

js中无明显的类与实例的划分，一般是通过对象的指向来创建类

一般来说是不用`__proto__`的

```
function Student(props) {
    this.name = props.name || '匿名'; // 默认值为'匿名'
    this.grade = props.grade || 1; // 默认值为1
}

Student.prototype.hello = function () {
    alert('Hello, ' + this.name + '!');
};//用这种方法创建新的对象时就不用创建一个新的函数，而是所有的对象共用一个函数

function createStudent(props) {
    return new Student(props || {})
}
```

## 浏览器

window

nabigator

screen

location

document:getElementById  getElementsByTagName cookie(服务器发过来应设置httpOnly属性)

history

### 操作DOM

选择某个节点

document

.getElementById

.getElementsByTagName

.getElementsByClassName

.children

.firstElemenChild

.lastElementChild

.querySelector

.querySelectorAll

#### 更新DOM

innerHTML#这个方法可以改变内部的子树，但会先删掉原来所有的子节点

```
// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置文本为abc:
p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
// 设置HTML:
p.innerHTML = 'ABC <span style="color:red">RED</span> XYZ';
// <p>...</p>的内部结构已修改
```

innerHTML,textContent可以对字符串进行编码，无法改变任何HTML标签

.style.修改css

#### 插入DOM

.前面的是父节点的目录

.appendChild 把一个子节点添加到父节点的最后一个子节点

```
var
    list = document.getElementById('list'),
    haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
list.appendChild(haskell);
```

```
var d = document.createElement('style');
d.setAttribute('type', 'text/css');
d.innerHTML = 'p { color: red }';
document.getElementsByTagName('head')[0].appendChild(d);
```

 动态增加一个子节点

.insertBefore 插在指定位置的前面

#### 删除节点

.removeChild(parent.children[索引])

注意：

var parent=document.getElementById('parent');parent.removeChild(parent.children[0]);parent.removeChild(parent.children[1]); // <-- 浏览器报错

浏览器报错：`parent.children[1]`不是一个有效的节点。原因就在于，当`<p>First</p>`节点被删除后，`parent.children`的节点数量已经从2变为了1，索引`[1]`已经不存在了。

因此，删除多个节点时，要注意`children`属性时刻都在变化。

### 操作表单

获取到这个节点

.value //获取用户输入的值，只用于text、password、hidden

.check判断是否勾上单选多选

设置值，直接设置.value值

### 提交表单

在submit控件里加入onclick="js函数名"

