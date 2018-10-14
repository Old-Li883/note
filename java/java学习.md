# java学习

## 面向对象三大特点

封装：隐藏细节模块化

继承：代码重用可扩展

多态：在代码中为同一名称的方法（接口）提供不同的实现，为一组类提供了统一的交互接口，又保留了类间的差异（统一接口，更便于扩展）

## 继承

java单继承

语法`public class Child extends Parent{}`

调用父类的构造函数`super()`

子类继承了父类中所有非private成员方法，及所有非private成员变量

方法的重写和重载

`final`关键字定义为不能继承，即该类为终类

慎用继承，少覆盖原则

### 向上转型

父类的声明子类的定义

向上转型可以操作子类继承和重写的方法，新增的不能

## 抽象类和方法

语法`public abstract class <classname>{}`

抽象方法`public abstract void draw();`

抽象类中不一定包含抽象方法，但是抽象方法的类必定是抽象类

抽象类的子类必须给出抽象类中的抽象方法的具体实现，除非该子类也是抽象类

## 静态方法及变量

静态变量在程序初始化时被创建，可以被该类所有的实例使用和修改

语法`public static 数据类型 变量名`

`public static 返回数据类型 方法名[形式参数列表]`

## 接口

语法`public interface 接口名 [extends 其他的接口列表] {}`

抽象方法的集合

接口隐式抽象的，声明接口不必使用abstract关键字

变量会被隐式指定为`public static final`

方法会被隐式指定为`public abstract`

接口提供了一组功能的命名集合，一个类通过实现接口的方式，获得接口方法（如果不是一个东西特有的动作，最好用接口，不要放在类中）

接口定义了不同类的交互标准（类似于类的方法被另一个类调用）

接口实现多继承

以接口名为声明类型的变量，可以被实现了该接口的任一类的对象赋值

## 多态

以接口实现多态

编译时的多态

运行时的多态，该引用变量具体调用哪个方法，在运行时才能确定

如何使用多态

1. 为一组类抽象出公共的父类或接口

   `Cat a = new Cat();`--->`Animal a = new Cat()`或者抽象出接口

   **注**：父类的声明的变量都可以new出子类

2. 之后将他们的方法名同一，在各个类中分别实现各个类的不同的方法

   ## 数组

   对象的数组的创建`Cat[] <name> = new Cat[10]`

   `Cat[][] mat {{new Cat(),new Cat()},{new Cat(),new Cat()}};`

## 类的定义

一个文件里只能有一个public类

文件名必须和public类名相同

## 类的关系

继承



关联：一个类作为另一个 类的成员变量出现（长期性）（例如：人用笔）（use-a）

聚合：聚合关系也是通过将其他类作为成员变量出现，与关联不同的是，两个类处于不同的层次上，一个代表整体，另一个代表部分（例如：车和轮子）（has-a关系）整体部分可分离，他们具有各自的生命周期。部分对象可以属于多个整体对象。

组合：组合关系也是通过将其他类作为成员变量实现，一个代表整体，一个代表部分，整体与部分是不可分离的，具有共同的生命周期，”同生共死“。组合要求普通的聚合关系中代表整体的对象负责代表部分对象的而生命周期，因此组合关系是不能共享的。就是代表部分的对象在每一时刻只能与一个对象形成组合关系，由后者负责生命周期。（contains-a）



依赖：A类方法使用到了另一个类B（最弱的一种形式）（临时性）

## UML

### 类图

矩形表示

上层：类名

中层：属性

下层：行为

### 创建类图

寻找类和确定类（及属性），提取名词或名词短语

提取动词或动词短语

找出类的关系

### 用例图

### 时序图

显示具体用例的详细动作或事件流程

水平维度：显示对象之间发送消息的时间顺序

垂直维度：显示发送消息的时间顺序

对象生命线：垂直虚线

对象激活狂：细长矩形

消息-----调用：实线段，实心箭头

        -----返回：虚线段，枝状箭头

顶部方框表示累的对象

#### 绘制时序图

确定事件流程

确定对象

添加对象生命线，发送的消息，激活矩形框

**学会善用抽象，把类中的共同地方抽象出来**

## 包与库

包名全部需要小写

### java.lang.Object类

成员方法：equals()判断是否为同一对象

toString():返回对象的字符串表示

### 包装类

基础类型的包装类，不能创建子类

包装类是不可变类，不可强制转换

数值类有两个静态方法valueOf(String s)用于创建包装对象 parsexxx(String s)用于将字符串转为对应的基本数据类型

自动包装------装箱、拆箱

### Random类

1. 创建Random对象

2. nextxxx调用伪随机数

## Java io

io Stream：一个数据序列

java.io几乎包含所有操作输入输出需要的类。Stream类代表输入源和输出目标

### 控制台io

#### 输入

java.io.InputStream

	java.io.FilterInputStream

		java.io.BufferedInputStream

1. 创建输入对象，`InputStreamReader cin = new InputStreamReader(System.in);`
2. 输入`int n = cin.read();`

#### 输出

`system.out.print`

java.io.Console

#### 输入

创建对象`Console con = System.console();`

输入字符串`String login = con.readLine("...")`

输入密码型的字符串`char [] password = con.readPassword("...")`

#### 输出

`con.printf(...)`

### 文件读写

1. 按字节读写：FileInputStream/FileOutputStream

2. 按字符读写文件内容：FileReader/FileWriter

3. 随机读写文件内容：RandomAccessFile

File类

File file1 = new File("文件路径")

#### 按字节读写

FileInputStream read(把read进来的值放入这个变量)方法

FileOutputStream write(把这个变量里的bytes输出到该对象绑定的文件)方法

记得 `.close`关闭

#### 按字符读写

FileReader read()方法

FileWriter wriet()方法

与字节读写类似

### 随机文件读写

1. 创建file对象

2. 创建随机文件读写对象RandomAccessFile对象

> `.read()`
>
> `.skipBytes()`跳过多少字节后再读
>
> `.read()`

### Buffer IO

BufferedReader,BufferedInputStream

Bufferedwriter,BufferedWriter

1. 创建方法`BufferedReader inputStream = new BufferedReader(new FileReader(文件名));`

把数据到内存中

### Scanner

读取String类型

以空格把数据流切割为token

token可以被不同的next方法转换为对应的数据类型

例：nextInt()

**附**：读取全部文件内容代码

>可以用.length()获取文件长度，创建对应的数组
>
>一般可以先用字节流读取，再通过new String来
>
>将其变为字符

## 字符串

### 创建方式

`String a = new String("...");`

也可以用char数组和byte数组初始化

### ==与equals的比较

### 字符串的存储方式

### 字符串查找

`indexOf()`

`lastIndexOf()`

通过参数的改变来实现方法的重载

### 获取字符

`.charAt(索引);`//获取一个字符

### 获取子串

`.substring(索引1,索引2);`//获取子串

### 字符串分割

`.split(String regex,int limit);`

### 字符串拼接

`String concat(String str);`

### 字符串变换

`String .trim();`切除空格

`.toLowerCase();`

`.toUpperCase();`

### 局部替换

`String replace(char oldChar,char newChar);`

`String replace(CharSequence target,CharSequence replacement);`

`String replaceALL(String regex,String replacement);`

`String replaceFirst(String regex,String replacement);`

## Java正则表达式

`Pattern`类，创建一个正则表达式对象，传入一个正则字符串

`Matcher`类是创建一个正则表达式匹配后返回的对象