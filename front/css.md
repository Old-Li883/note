# css

语法规则：选择器+多条声明

例：`p{color:red;text-align:center}`

注释：

`/*   */`

## id和css选择器

id选择器可以为标定特有id的html元素指定特定的样式

以#开头，例：id="para1":

`#para1`

{

​	`text-align:center;`

​	`color:red;`

}

class选择器

class 选择器用于描述一组元素的样式，class 选择器有别于id选择器，class可以在多个元素中使用。

class 选择器在HTML中以class属性表示, 在 CSS 中，类选择器以一个点"."号显示：

在以下的例子中，所有拥有 center 类的 HTML 元素均为居中。

实例

.center {text-align:center;}

## css创建

css中插入样式表有三种方法：

* 外部样式`<link rel="stylesheet type="text/css href"mystyle.css`
* 内部样式
* 内联样式

## css背景

- background-color
- background-image
- background-repeat
- background-attachment
- background-position

##  文本

颜色：color

对齐方式：text-align

文本修饰：text-decoration

文本转换：text-transform

文本缩进：text-indent

## 字体

字体样式：font-style

字体大小：font-size

字体大小：font-size以em为单位，1em=16px

## 附.与：使用

.是一个选择有.的话是要用class选择这一个东西，如果没有.只定义p的话，所有的p都是这种东西。

:我现在的理解是一种状态的标识，就是在这个状态下这个东西用这种样式

## 链接样式

a:link {color:#000000;}      /* 未访问链接*/*

a:visited {color:#00FF00;}  /* 已访问链接 */ 

a:hover {color:#FF00FF;}  /* 鼠标移动到链接上 */ 

*a:active {color:#0000FF;}  /* *鼠标点击时 */

注意：

- a:hover 必须跟在 a:link 和 a:visited后面
- a:active 必须跟在 a:hover后面

## css列表

list-style-type

标记图像

list-style-image

## 盒子模型

理解margin，border，padding，context

![CSS box-model](http://www.runoob.com/images/box-model.gif)

border边框设置（可查）