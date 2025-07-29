# 7：java学习笔记：while循环语句
之前都是for循环结构，那么在循环结构中有其他的一个循环，这个循环语句就是while循环。

## 6.1while循环结构
### 6.1.1while循环的基本结构
```java
while (循环条件) {
    // 循环体
}
```
因为for循环与while循环作用本质上是一样的，都是循环语句，所以几乎所有for循环能写的地方，while循环也能写，但是结构不一样。

首先还是经典的

1. 如果打印出来1--100这几个数字呢？

```java
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int i=1;
		while(i<=100) {
			System.out.println(i);
			
		}

	}
}
```
其实和for循环中的三要素都有。

第一，初始值，（int i = 1）只是写在外面而已。

第二，循环的条件，循环的条件满足了，才能进入循环并且执行代码。

第三，（这里是while非常容易错的点）（上面这个代码也是错的）i的增值与减值，很多人都写到输出就结束了，但是在这里如果不写增值的话，会陷入死循环，因为如果不写上的话

i=1（一开始）判断一下能不能进入循环（i<=100)当然可以进入循环，然后执行代码块的代码，打印出来了1（i的值）那么循环结束，再次判断i是不是<=100，i并没有增加或者减小，所以它一直满足，一直循环。

所以必须在后面写上i++

正确的代码：
```java
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int i=1;
		while(i<=100) {
			System.out.println(i);
			i++;
		}

	}
}
```
输出的话
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/cbf1eec173eb4206adb24575dfadfec4.png" width="600"/>
</p>

所以，在while中非常重要的就是增值（或者减值）如果忘记了将会陷入死循环。

2.在while循环中计算1到100之间所有偶数和

那么1--100，首先构建基本的while循环

```java
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int i=0;
		while(i<=100) {
		}

	}
}
```
这个就是基本的while循环的框架，然后呢需要偶数和，需要偶数，同样也需要他们全部加起来，所以需要创建一个变量来进行加，创造一个sum

```java
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int sum = 0;
		int i=0;
		while(i<=100) {
			sum+=i;
			i+=2;
		}
	}
}
```
当i=0的时候满足while的循环判断，sum（旧的）+i（i=0）=sum新的=0

完成之后，需要将i+=2(这个的含义是，每次增加2)

i+=2 =>i=2(新的）

这里结束了第一次循环，第二次循环i=2，符合我的循环判断标准，继续循环

i=2, sum（旧的（上一轮循环的）=0）+i（i=2) = sum（新的 = 2)

i+=2=> i+2 = 4（新的）

结束了第二次循环，依次类推

到i=100,（符合我的循环判断标准)

进入循环，sum（旧的=2450）+i（i=100）=sum（新的=2550）

然后i+=2=> i+2=102;

那么这个102不满足循环判断语句，所以不能进入循环，整个代码结束了，但是没有任何输出，为什么？因为你没有写print，那么这个句子写在哪里呢？如果写在循环体里面的话，每次输出都有一个数字，如果只想要一个数字的话，必须写在while循环结束了，sum已经完成了很多次加法运算之后才可以。

那么通过括号能够判断哪里是while循环代码块的地方

​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/21fe36c6fbd74d479cc0575236e39ac3.png" width="600"/>
</p>

通过按一下下面的右括号 eclipse可以显示上面的括号，那么左括号右括号中间就是整个代码块，是while统治下的代码块，我们如果不想要有很多数字的话应该等到代码块结束，也就是在这个右括号的旁边写好，这样才能打印出来是一个数字。

```java
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int sum = 0;
		int i=0;
		while(i<=100) {
			sum+=i;
			i+=2;
		}
		System.out.println(sum);
	}
}
```
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/84663fddb2b448818a94828288991870.png" width="600"/>
</p>

## 6.2while（true）
while（true）非常好用，也很常用，while（true）指的是不断的循环，直到代码让它停止为止，并且没有条件。

所以非常常用。

通过一个例子来知道while(true)如何使用

输入有多少学生，然后问学生多少成绩，然后输入quit能退出，最后计算有几个人及格。

那么我们来分析一下这个题目，”输入有多少学生，然后问学生多少成绩，然后输入quit能退出，最后计算有几个人及格。“
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		System.out.println("有几个学生呢？ ");
		int number = input.nextInt();
		
		
	}
}
```

这个学生是多少成绩，如果你写3个学生，你怎么写用户交互的问题，比如说第一个学生的成绩是90，第二个学生成绩是88，第三个学生成绩是79，那么需要写出第几个学生，不然很容易混乱，所以这个用户交互的问题需要写在while(true)中。同样在这里还有一个棘手的问题是需要输入quit退出。

所以我改变了一般用户交互的形式。
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			
		}
		
		
	}
}

```
我写成这样，首先我每次问有几个学生的问题的时候，如果输入了quit那么我的整个循环结束，如果输入数字的话继续进行，我把n的数据类型变成了string。

那么接下来是条件语句，因为要看我输入的是不是quit不是的话，那么进行数字的部分，如果是的话直接退出循环那么有两个问题：

第一个问题 如果判断String能不能和quit一样呢，String使用equals来对比，而这个equalsIgnoreCase指的是 不用管是大小写，只要输入的东西是一样的话就行。

第二个问题 怎么样退出这个while(true）的循环，使用break 输入break就能直接退出循环。

所以写if条件语句
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {//String的对比，n与quit一不一样
				System.out.println("谢谢使用，再见");
				break;
			}
		}
		
		
	}
}
```
那么我的第一步做完了。接下来写如果我输入的不是qiut，如果是数字的话怎么办呢，而n不是数字，我应该怎么继续呢？

那么我需要把string改变成int类型，怎么操作呢
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {
				System.out.println("谢谢使用，再见");
				break;
			}
			int student = Integer.parseInt(n);
			
		}
		
		
	}
}
```
那么这个就是转换的代码，如果想要从string改变成int那么就需要这个代码（在parseInt（））括号里面的是需要变换的变量名称，那么变化成int student这个变量，如果你输入3，那么其实变量是进入到了student=3（student是变量，3是值）

那么有student的值了，也就是知道了有几个人了，那么我是不是可以使用for循环了。
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {
				System.out.println("谢谢使用，再见");
				break;
			}
			int student = Integer.parseInt(n);
			for(int i =1 ; i<=student; i++) {
				
			}
		}
		
		
	}
}
```
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {
				System.out.println("谢谢使用，再见");
				break;
			}
			int student = Integer.parseInt(n);
			for(int i =1 ; i<=student; i++) {
				System.out.println("第 " + i + "的学生考的成绩是多少呢 ");
//这里就是第i个，那么i等于1的话那么输出就是第一个学生怎么样怎么样
				double grade = input.nextDouble();
			}
		}
		
		
	}
}
```
这里就是可以让你每次输入第一个人的成绩怎么样，第二个人的成绩怎么样，但是如果用户输入了一个-10，成绩不能是负数，所以我们需要把它叉出去。
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {
				System.out.println("谢谢使用，再见");
				break;
			}
			int student = Integer.parseInt(n);
			for(int i =1 ; i<=student; i++) {
				System.out.println("第 " + i + "的学生考的成绩是多少呢 ");
				double grade = input.nextDouble();
				if(grade<0) {
					System.out.println("重新输入，谢谢，不能是哦！");
					
				}
			}
		}
		
		
	}
}

```
那么到这里分析出来一个问题，如果这个输出之后，用户不小心输入了一个-10，然后判断出来是错误的，但是在这个for循环中，会认为 用户第一个学生的成绩已经完成了，这个显然是不正确的，我第一个学生的成绩不能是-10啊，所以需要使用到continue，这个数值不会记录在册但是还是会跳过第一个.因为我的第几个 都是要i来计算的，i每一轮都需要+1 这个是for循环中的三要素，如果我想要重新输入一次怎么办呢，这里i已经是等于1了，那么如果需要重新输入，i-1然后i就变成0了，这样在经过for循环的三要素的时候0<student，可以进入for循环的循环体，然后呢i原来是0+1 还是1，你可以有第二次输入机会了。

同样在题目中需要使用到平均数，所以我必须要计算，sum（和值）所以需要一个sum
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {
				System.out.println("谢谢使用，再见");
				break;
			}
			int student = Integer.parseInt(n);
			int sum = 0;
			for(int i =1 ; i<=student; i++) {
				System.out.println("第 " + i + "的学生考的成绩是多少呢 ");
				double grade = input.nextDouble();
				if(grade<0) {
					System.out.println("重新输入，谢谢，不能是哦！");
                     i--;
					continue;
				}else {
					sum+=grade;
				}
			}
		}
		
		
	}
}
```
和知道了之后，我们计算平均值需要除以有几个数字，这个是student中用户自己输入的。

位置的话，必须是在for循环完全结束之后才行，不然的话，用户输入一个成绩，它就会算一次平均数，这显然是不正确的。

所以代码是
```java
import java.util.Scanner;
public class we {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		while(true) {
			System.out.println("有几个学生呢？ ");
			String n = input.next();
			if(n.equalsIgnoreCase("quit")) {
				System.out.println("谢谢使用，再见");
				break;
			}
			int student = Integer.parseInt(n);
			double sum = 0;
			for(int i =1 ; i<=student; i++) {
				System.out.println("第 " + i + "的学生考的成绩是多少呢 ");
				double grade = input.nextDouble();
				if(grade<0) {
					System.out.println("重新输入，谢谢，不能是哦！");
					i--;
					continue;
				}
				if(grade>=0){
					sum+=grade;
				}
				
		}
			double average = sum / student;
			System.out.println("这几个学生的平均成绩是 " + average);
		}
		
		
	}
}
```
在这个代码中还有小瑕疵，sum最好改成double（因为grade是double数据类型）
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/92b7ab415104449987a34d89fe08eef8.png" width="600"/>
</p>

如果输入一个负数的情况呢
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/404535ade9dd469a9aac4078c4539400.png" width="600"/>
</p>
怎么样退出这个循环呢？输入quit
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/6fc436a7b7a5478cbb3a713dbf952375.png" width="600"/>
</p>

最后登出了系统，然后代码结束了。

但是在这里，这一个代码中，还是不能满足，因为代码有问题，这个问题将会在下一篇文章中仔细的讨论。