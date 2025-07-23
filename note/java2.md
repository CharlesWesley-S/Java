# 2:java的介绍与基础2：Scanner
## 2.1Scanner
### 2.1.1引入问题
现在Java可以输入具体的数字，但是我们没有办法可以随机输入一些数字，然后进行一些计算或者进行一些比较处理。

在python中我们经常使用 input语句，可以来看一个例子。
```python
a=int(input(" give me a number"))
b=int(input("give me another number"))
if a >b:
    print("a>b")
elif a==b:
    print("a=b")
else:
    print("a<b")
```
这个可以随便的输入一个数字，然后进行比较，但是在Java中，我们还没有学过怎么随机输入数字（这个比较的话会在后面的语句中介绍的）。
```java

public class mean {
    public static void main(String[] args) {
        int _abc=3;
        int a=2;
        System.out.println(_abc+a);
    }
    
}
```

额不要管这个文件名字，mean（平均数）没算平均数，我这个只是想说我们现在只能使用数字，不能随意输入数字。

这个就需要Scanner来进行操作了，但是在Java中scanner是一个类。（class）

### 2.1.1scanner实现可以随意输入数字
首先，他是一个类，所以我们需要先导入这个类。
```java
import java.util.Scanner;
```
然后
```java
import java.util.Scanner;
public class odd {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        // 读取用户输入的整数
        int r = input.nextInt();

       
    }
}
```
这个前面的三行大家应该都知道是啥意思，这个第一行是引入，第二第三行也老熟悉了。

首先来看一下右边的new Scanner（System.in）的意思指的是 我创建了一个新的Scanner 通过（System.in）进行输入系统。

而左边input Scanner 指的是我用input语句调用了Scanner这个对象。然后接下去的那一行就是我可以随机输入一个数字进入我r这个变量去了。

然后注意这里使用的是nextInt ，所以接下来r必须是int而不是double。 如果你想使用double的话可以使用nextDouble.

如果我想要计算随机一个r的圆的周长与面积的话。这个代码是这样的。
```java
import java.util.Scanner;
public class odd {
    public static void main(String[] args) {
        System.out.println("what's the radius you wnat to calculate");
        Scanner input = new Scanner(System.in);
        // 读取用户输入的整数
        double r = input.nextDouble();
        System.out.printf("you want to calculate the circle about:r= %f \n",r);
        final double PI= 3.1415;
        double square = PI * r*r;
        double perimeter = 2* PI * r;
        System.out.printf("the raduis %f circle's square and the perimeter is %f and %f ",r,square, perimeter);
    }
}
```
首先来问一下你需要啥radius（半径），然后像刚才一样，调用了Scanner的对象，然后创建一个新的Scanner类。然后把这个要随机输入数字的类放进了一个r中，所以再终端中首先会出来一个
然后输入你想要多少半径的圆 计算面积与周长。
<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/0164bc8bc5ef41fd837393ed95624e0b.png" width="600"/>
</p>

再代码中那个final指的是常量的意思，是不能改变的，（常量使用大写）。这个不准确。

然后再终端再回车一下就能出来结果了。