# 8：java学习笔记：try-catch语句
​
在上一片篇中写到了7 中最后的代码，那么并没有结束。

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
再解释一下，在这个代码中呢，用户可以输入有多少个学生，然后每次输入，都可以输入一个学生的成绩，并且在这个代码中，也有一定的健壮性（健壮性，代码健壮代表的是代码是健康的没有什么漏洞，比如说如果用户输入了-100，但是在代码中没有排除这一情况，那么这个代码就是有问题的，成绩不能是负数！！）

## 8.1第一个问题
但是在这里的代码中是有一定的健壮性，不是非常健壮，在这个代码中是有问题的，第一既然考虑到了成绩是不是负的，那么人数呢？人数肯定不能是负数，在生活中说-9个人，显然是错误的，但是在这个代码中并没有考虑到。

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
			if(student <0) {
				System.out.println("人数不能是零！！ ");
				continue;
			}
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
这个就解决了第一个健壮性的问题，在进入for循环之前，加入一个if语句，判断一下用户输入的是不是正数，如果是的话，那么继续进入，当然这里的变量名称必须是使用student（这个时候已经从String类型变成了int类型，String类型是为了写quit的。

用户的体验感就是
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/907b054999d145e2b3c715f0468ddc75.png" width="600"/>
</p>

用户输入了-2，那么抱歉，人数不能小于零。那么代码的健全性进一步增加。

## 8.2try-catch语句
第二个问题，是需要使用try-catch语句的。

​​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/5707731b644f41c1860f0032a4e112c8.png" width="600"/>
</p>

如果在第几个学生这里（当我的变量变成int类型的时候）

如果不小心输入了英文字母，代码就会全面崩溃，在实际中用户不小心输入了英文字母，只会有提示，而不是系统的全面崩溃，所以代码的健全性还不是非常充足。

所以需要使用到 try-catch语句，try-catch语句使用来捕捉错误的，比如说用户在这里输入了一个英文字母或者中文的话，它能捕捉到异常，并且不会让系统崩溃。

8.2.1java的常见异常与try-catch语句
1：NumberFormatException

字符串转数字失败，这也是最常见的数字异常之一，这是转换会出现的异常，上面的代码，使用了转换（从String到int类型）所以每次使用转化都需要try-catch抛出numberFormatException这个异常。

所以需要使用try-catch语句，try-catch的基本结构
```java
try{
    //代码
}catch(代码可能抛出的异常){
    //输出是什么异常，提醒一下用户，知道自己可能输入错误导致犯错等等
}
```
这个异常举一个例子
```java
public class Price {
    public static void main(String[] args) {
        String str = "abc123";  // 不是纯数字，无法转换

        try {
            int num = Integer.parseInt(str);  // ❌ 会抛出 NumberFormatException
            System.out.println("转换成功：" + num);
        } catch (NumberFormatException e) {
            System.out.println("出错啦！无法将字符串转换为整数！");
        }
    }
}
```
str本身不是纯数字，转化肯定会抛出错误。所以结果就是
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/749dba7a84874dacbfa5f28ddb77314c.png" width="600"/>
</p>

2：ArithmeticException

这个也是常见的数字异常类型，这个类型的异常是：除以零的情况。

显然10/0是错误的，所以需要使用一个try-catch抛出，用户一定知道自己犯错了，可能不小心导致的，所以代码是
```java
import java.util.Scanner;
public class Price {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
         
        try {
        	System.out.println("输入一个数字");
            int num = input.nextInt();
        	System.out.println("输入一个被除数");
        	int num2 = input.nextInt();
        	int num3 = num/num2;
            System.out.println("最后的结果是 " + num3);
        } catch (ArithmeticException e) {
            System.out.println("出错啦！！ 被除数不能是0哦，抱歉啊");
        }
    }
}
```
在这个代码中，如果你的num2输入了0，那么就会抛出异常。

可以看一下运行的结果。
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/497952915ac14eca844b7f45e715bbbd.png" width="600"/>
</p>

同样在之后的io流array中会有更多的异常出现的。

tips：这里的异常不是错误，错误try-catch抛不出来，异常不是代码本身的错误，代码是正确的，不过输入的时候一不小心错误了，导致的代码异常。错误指的是代码本身逻辑错误，比如说这个代码的逻辑是错误的，那么使用try-catch也没用，try-catch不是神，只能帮你做一点保障工作。

3：InputMismatchException

input输入的意思，mismatch不一样，就是输入异常的意思，比如说需要用户输入double类型，但是用户输入了string类型的，当然这个不行，所以这个也是一个异常。
```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class Price {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        double number = 0;

        while (true) {
            System.out.print("请输入一个小数（例如 3.14）：");

            try {
                number = input.nextDouble();  // 会抛出 InputMismatchException
                break;  // 输入成功，跳出循环
            } catch (InputMismatchException e) {
                System.out.println("⚠️ 输入错误，请输入合法的小数！");
                input.next();  // 清除错误输入，避免死循环
            }
        }

        System.out.println("你输入的是：" + number);
    }
}
```
在这里需要输入一个double类型，如果输入一个整数，没有问题，整数类型是直接处理为1.0这样，但是不能输入字符串类型，字符串类型输入abc，就出错了，在这个代码中有input.next（）所以消除了错误的输入，然后while（true）重新开始，用户重新输入。
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/a366138fd46048689813a6769470d128.png" width="600"/>
</p>

如果一个代码中可能出现很多的异常的话，可以连续使用try-catch来帮助你，格式的话可以举一个例子来看。
```java
import java.util.Scanner;

public class Price {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        try {
            System.out.print("请输入一个整数字符串：");
            String input = sc.nextLine();
            int num = Integer.parseInt(input);  // 可能抛出 NumberFormatException

            int result = 10 / num;              // 可能抛出 ArithmeticException
            System.out.println("10 除以你输入的数 = " + result);

        } catch (NumberFormatException e) {
            System.out.println("输入不是合法的整数！");
        } catch (ArithmeticException e) {
            System.out.println("不能除以 0！");
        } catch (Exception e) {
            System.out.println("发生了其他未知错误：" + e.getMessage());
        }
    }
}
```
在这里如果你输入了一个字母字符串的话，抛出来的异常就是，输入不是合法的整数！（抛出的就是NumberFormatException这个错误，那么如果这个数字是零的话，它是一个数字，但是因为有除法所以必须有一个ArithmeticException。那么最后一个exception是什么，是帮着兜底的，exception指的是未知的异常，它可以抛出，发现了一个异常但是不包括在前面两个异常类型中，它是用来兜底。所以写在最后，最后兜底，不让异常让系统崩溃。
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/816c43b3def74afc9567516093dcaaee.png" width="600"/>
</p>

### 8.2.2之前代码的问题
回到之前学生系统的代码，那么转化的时候会有NumberFormatException这个类型的错误，所以是以哦那个try-catch保护一下。
```java
import java.util.InputMismatchException;
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
			try {
				int student = Integer.parseInt(n);
				double sum = 0;
				if(student <0) {
					System.out.println("人数不能小于零！！ ");
					continue;
				}
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
			}catch(NumberFormatException e) {
				System.out.println("不能随便输入字母哦，只能是数字！！");
			}catch (InputMismatchException e) {
                System.out.println("⚠️ 输入错误，请输入合法的小数！");
                input.next();  // 清除错误输入，避免死循环
            }catch(Exception e) {
            	System.out.println("出现错误，" + e.getMessage());
            }
			
		}
	}
}
```
在这个代码中有两个可能出现的异常，第一个很简单是String变化成int的时候出现的异常，第二个是在询问第几个学生有是多少分的时候，如果我输入了一个英文或者中文字母的话，也可以抓住异常，同样使用exception兜底。

同样e.getMessage()，指的是，抓住不是之前的异常，并且打印出来异常的类型。