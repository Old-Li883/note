# html

标记语言

标签通常成对出现

head部分通常写一些元数据

只有body页面网页才会显示

<!DOCTYPE html> h5声明

`<meta charset="UTF-8">`输出中文的声明

标题`<h1>`----`<h6>` `<hr>`在标签下加下划线

段落`<p>``</p>`

链接`<a>`标签

例：`<a href="http://www.runoob.com">连接名</a>`

target属性"_blank",链接将在新窗口打开

图像`<img>`

例：`<img src="图片路径" width="  " height=" "/>`

`<br>`但个标签表示换行

HTML的属性一般在开始标签中

`<!--一个注释-->`

## HTML 文本格式化标签

真实的标签是tag后面的那一个，通常是单个标签

| 标签                                               | 描述         |
| -------------------------------------------------- | ------------ |
| [](http://www.runoob.com/tags/tag-b.html)          | 定义粗体文本 |
| [](http://www.runoob.com/tags/tag-em.html)         | 定义着重文字 |
| [](http://www.runoob.com/tags/tag-i.html)          | 定义斜体字   |
| [](http://www.runoob.com/tags/tag-small.html)      | 定义小号字   |
| [](http://www.runoob.com/tags/tag-strong.html)     | 定义加重语气 |
| [](http://www.runoob.com/tags/tag-sub.html)        | 定义下标字   |
| [](http://www.runoob.com/html/m/tags/tag-sup.html) | 定义上标字   |
| [](http://www.runoob.com/tags/tag-ins.html)        | 定义插入字   |
| [](http://www.runoob.com/tags/tag-del.html)        | 定义删除字   |

## HTML "计算机输出" 标签

| 标签                                         | 描述               |
| -------------------------------------------- | ------------------ |
| [](http://www.runoob.com/tags/tag-code.html) | 定义计算机代码     |
| [](http://www.runoob.com/tags/tag-kbd.html)  | 定义键盘码         |
| [](http://www.runoob.com/tags/tag-samp.html) | 定义计算机代码样本 |
| [](http://www.runoob.com/tags/tag-var.html)  | 定义变量           |
| [](http://www.runoob.com/tags/tag-pre.html)  | 定义预格式文本     |

## HTML 引文, 引用, 及标签定义

| 标签                                               | 描述               |
| -------------------------------------------------- | ------------------ |
| [](http://www.runoob.com/tags/tag-abbr.html)       | 定义缩写           |
| [](http://www.runoob.com/tags/tag-address.html)    | 定义地址           |
| [](http://www.runoob.com/tags/tag-bdo.html)        | 定义文字方向       |
| [](http://www.runoob.com/tags/tag-blockquote.html) | 定义长的引用       |
| [](http://www.runoob.com/tags/tag-q.html)          | 定义短的引用语     |
| [](http://www.runoob.com/tags/tag-cite.html)       | 定义引用、引证     |
| [](http://www.runoob.com/tags/tag-dfn.html)        | 定义一个定义项目。 |

## html头部

`<title>`文档标题

`<base>`基本的链接地址

`<link>`定义文档与外部资源的关系

例`<link rel="stylesheet" type="text/css" href="shenmeshenme.css">`

`<meta>`定义元数据

`<scrpt>`加载脚本文件

## 图像

单标签`<img src="">`

alt当图像无法加载是显示的文字

width,height图像的高度和宽度

设置图像链接,也可以按区块设置图像链接

## 表格

`带有标题的表头<caption>`

`colgroup>列属性`

`<table></table>`

`<th></th>`表头

`<tr></tr>`行

`<td></td>`每行的元素

## 列表

`<ul><li></li></ul>`无序列表

`<ol><li></li></ol>`有序列表 属性type定义不同风格的列表项

## 区块

`<div></div>`区块

区块元素组合在一起使用，如：<h1>,<p>,<ul>,<table>

`<span></span>`内联元素如css

内联元素组合在一起使用，如：<b>,<td>,<a>,<img>

## 布局

<div>布局

<table>布局

区块布局感悟:默认应该是竖排,

如果设置了float属性,光标位置不变,但如果下次排列横排范围超过了父级区块范围,就往下排

注意:clear属性好像可以移动光标的位置`clear:both`例子这样就可以使光标下移

## 表单

`<form></form>`

文本域

<form> First name: <input type="text" name="firstname"><br> Last name: <input type="text" name="lastname"> </form>

密码字段

<form> Password: <input type="password" name="pwd"> </form>

单选按钮

<form> <input type="radio" name="sex" value="male">Male<br> <input type="radio" name="sex" value="female">Female </form>

只有name一样才能单选

复选框

<form> <input type="checkbox" name="vehicle" value="Bike">I have a bike<br> <input type="checkbox" name="vehicle" value="Car">I have a car  </form>

提交按钮

<form name="input" action="html_form_action.php" method="get"> Username: <input type="text" name="user"> <input type="submit" value="Submit"> </form>

input类型

range

search

tel

time

url

week



## h5

* 可以支持写数学公式
* 支持拖拽(用js)
* 可以进行定位(时间较长)
* h5有自己的控件支持