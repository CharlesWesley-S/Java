# 1:java的介绍与基础1：变量，数据类型与数学运算符
## 1.1Java的开始
从今天开始，我将更新一下关于学习Java的笔记，文章，希望大家支持。这个Java吧，感觉本质上逻辑始于python很类似，但是吧它的表达更加繁琐难懂，所以我还是喜欢python，比较简介明了。但是Java的功能也是非常实用。所以在这个专栏中开始写一些关于Java的文章。

但是在这篇文章中并不阐述Java安装的过程，直接从基础的知识点开始写。

注意Java的文件后缀是.java（想.py一样是强制要求的，不能更改）同样在这里我还是实用了vscode编辑器进行编程的编辑。

## 1.2Java的基础1
在这篇文章中，直接开始写Java的基础知识点，它与python的基本逻辑是差不多的，但是在表达上会有很大的差异，并且学了python之后的人来学习Java，会发现哇，感觉好复杂好厉害

这个是python的hello world编程

```python
print("hello world")
```
这个是Java的hello world
```java
public class hello {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```
所以两者是有一定的区别的，但是本质的东西并没有改变。逻辑其实是差不多的，理解了python中的一些东西，Java的很多东西也很容易理解（python我会继续更新的）

编程Java的时候呢，与编程python有一点不一样，就是Java的文件名称必须与第一行class后面的hello一摸一样这样才能运行。所以我这个文件必须叫做hello并且大小写也必须一样。

<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/577501582b314b22bbd3d1827d065c81.png" width="500"/>
</p>
文件名就是hello。

### 1.2.1对于代码的详解与一些转义符号
#### 1.2.1.1代码的详解
这里首先来详细的讲一下这个代码

第一行
```java
public class hello{}
```
你可以怎么理解这个，就是固定格式，代表这个代码是Java，前面的 public class 是不能改变的。后面的那个单词应该是文件名。

第二行
```java
public static void main(String[] args) {}
```
这个一行单词其实也不能改，main是一个函数，代表java会从我这里开始，代表的是我的程序从这里开始（我们一般称它为入口点）。还有一个作用是：接收命令行参数，main函数的参数是一个字符串数组 (String[] args)，它用于接收命令行参数。这些参数可以在程序启动时传递给程序，以便程序根据不同的输入做出不同的响应。

第三行
```java
System.out.println("Hello World");
```
这句话中就比较好理解了，它翻译成中文的意思就是系统输出（system.out)，并且打印在终端上，那我们的终端就会显示hello world。

第四行，第五行代表的是内层框架与外层框架。

这个就是基本的Java程序。

#### 1.2.1.2转义字符
首先来介绍一下println这个函数与print的区别

来看一下这个代码：
```java
public class hello {
    public static void main(String[] args) {
        System.out.print("Hello World");
        System.out.println("你好世界");
        System.out.print("hello java");
    }
}
```
在Java中print与println都能使用但是，println就是换行的意思。可以看一下
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/166fb4b6d12743868fed5318eda970c6.png" width="600"/>
</p>

可以看到这个println不是让自己这一行换行，是让下一行换行。这个与转移字符中的\n很像（与python是一样的）

举个例子来看看
```java
public class hello {
    public static void main(String[] args) {
        System.out.print("Hello World \n");
        System.out.println("你好世界");
        System.out.print("hello java");
    }
}
```
这样子打印出来的hello world 与你好世界就分成了两行。
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/d7870aec7fc5411f890e6a3bca8119bd.png" width="600"/>
</p>

所以\n的python与Java都是一样的，同样还有一个空格的字符\t。

可以这样使用：
```java
public class hello {
    public static void main(String[] args) {
        System.out.print("Hello\tWorld \n");
        System.out.println("你好世界");
        System.out.print("hello java");
    }
}
```
我将hello world中间的空格删掉然后加上了\t。

结果就是：
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/06ae591c4a72430f80b53c0a79de84a3.png" width="600"/>
</p>

​
### 1.2.2Java的变量与数据类型
Java的变量，数据类型与python的异曲同工之妙，这里没有python基础的可以先去看一下我写的

2：python第二章：python语法基础1（适合小白学习）-CSDN博客

#### 1.2.2.1Java的变量
首先来看一下Java中的变量，说实话这个变量与python可以说是很像，但是还是有一定区别的。

（注意这里没有说的区别，就是一样的）

首先Java是静态语言，python是动态语言，所以Java不能随便的改它本身的数据类型。有一些数据类型的转变是需要用代码改变的。

还有就是表示变量的方式不一样（这个会在等一会儿讲到）

#### 1.2.2.2Java的数据类型
Java中的数据类型与python中也非常相似，但是也有不一样的地方，并且Java表示变量的语法与python很不一样。

##### 1.2.2.2.1int整数型
首先介绍一下整数型，与python一样就是单纯数学中整数的意思。

但是表示的时候要遵守：数据类型 变量名称=变量的值 这样子的格式来进行。
```java
public class mean {
    public static void main(String[] args) {
        int _abc=3;
        System.out.println(_abc);
    }
    
}
```
int就是变量的数据类型，_abc就是变量名称，然后3就是变量的值。

##### 1.2.2.2.2 string字符串型
这个与python也一样，所以不做多的赘述。然后给出一个例子。（string在写的时候需要大写）
```java
public class mean {
    public static void main(String[] args) {
        int _abc=3;
        String a="你好";
        System.out.println(_abc);
        System.out.println(a);
    }
    
}
```
然后输出就是
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/8ab44b562d974663a66f37d75ee49b9a.png" width="600"/>
</p>

##### 1.2.2.2.3 char类型
这个就与python不一样了，python中没有这个数据类型，这个数据类型呢，也非常的简单。string是引号中多个字符，char是在引号中只有一个字符。并且这个char只能使用单引号‘’

看一下例子
```java
public class mean {
    public static void main(String[] args) {
        int _abc=3;
        String a="你好";
        char b='x';
        System.out.println(_abc);
        System.out.println(a);
        System.out.println(b);
    }
    
}
```
这里char使用单引号就会报错（这点和python很不一样，因为python的语法较为混乱，但是Java的语法更为严格）

打印出来就是
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/219abd1460654fc9821c427fc33ea970.png" width="600"/>
</p>

##### 1.2.2.2.4double型
这里可以将double型与python中的float型说成一个类型，但是这里要注意Java也有自己的float只是精度与double不一样，可以这么说，double精度更高。

然后可以举一个例子
```java
public class mean {
    public static void main(String[] args) {
        int _abc=3;
        String a="你好";
        char b='x';
        double w=0.34;
        System.out.println(_abc);
        System.out.println(a);
        System.out.println(b);
        System.out.println(w);
    }
    
}
```
这个就是double类型的数字。

结果就是：
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/308d36e46def46a0bb1ff133b6690595.png" width="600"/>
</p>

### 1.2.4Java的数学运算符
Java的运算符与python也有异曲同工之妙，几乎一样
| 运算     | 数学符号             | Java 表达式           | Python 表达式        |
|----------|----------------------|------------------------|-----------------------|
| 加法     | +                    | `a + b`                | `a + b`               |
| 减法     | -                    | `a - b`                | `a - b`               |
| 乘法     | ×（或写成 *）         | `a * b`                | `a * b`               |
| 除法     | ÷（但计算机中写作 /）  | `a / b`（结果是整数）   | `a / b`（结果是小数）  |
| 取整除   | ⌊a/b⌋                 | `a / b`（int 类型）     | `a // b`              |
| 取余     | mod（或 %）           | `a % b`                | `a % b`               |
| 乘方     | 幂符号（如 a²）        | `Math.pow(a, b)`       | `a ** b`              |

​