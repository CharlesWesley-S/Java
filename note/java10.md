# 10：java学习笔记：function（方法）（基础篇）
## 10.1java方法
通过一个简单的例子，来看方法的组成原理：
```java
public class Example {

    // 定义一个返回类型为 int 的方法，方法名为 add，接受两个 int 类型的参数
    public int add(int a, int b) {
        // 方法体，执行加法操作并返回结果
        return a + b;
    }

}
```
中间的就叫做方法，这个方法是输出int类型的，并且有两个参数（a与b两个参数）然后呢最后返回值是a+b。

### 10.1.1方法的组成部分
1. 返回类型：方法返回值的数据类型。如果方法不返回任何值，则使用 void 关键字。（void关键字代表的是不返回任何值）如果有static就说明是静态代码。
2. 方法名：标识方法的名称，遵循命名规则。
3. 参数列表：方法接受的参数，多个参数用逗号分隔。
4. 方法体：包含要执行的代码块。

```java
public class Greeting {
    // 定义一个返回类型为 void 的方法，方法名为 sayHello，不接受任何参数
    public void sayHello() {
        // 方法体，打印问候语
        System.out.println("Hello, World!");
    }
}
```
这个方法就是输出了 hello，world问候语。并且没有任何的参数，知识打印出来一个hello，world。

## 10.2 function的使用与区别
### 10.2.1静态方法
首先在java的方法中，有静态方法与非静态方法，静态方法较为简单，调用比较方便。
```java
import java.util.Scanner;
public class d {
	
	public static int add(int a,int b) {
		int sum = a+b;
		return sum;
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		System.out.println("你想要输入的第一个数字是 ");
		int num1 = input.nextInt();
		System.out.println("你想要输入的第二个数字是 ");
		int num2 = input.nextInt();

		System.out.println("两个数字的和是 "+add(num1,num2));

	}

}
```
这个是基本的代码，首先在class中建造一个方法（static 表示的是静态）所以在main之前构造了这个代码的核心算法，这个是比较常见的写法，在main中一般只写基本的用户交互与基本的输出输入。

因为是静态的方法，所以调用只要写方法名（后面加上参数（如果有的话））

在这个代码中首先输入了两个数字，并且通过add传参传入a与b中，在方法中a+b所以输出了sum，那么这个代码就是两个数字的和。

​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/28c7147b98ef498183cb68be69c6d9e3.png" width="600"/>
</p>

那么不是int 如果是静态方法的double呢，我们使用double的静态方法写一个小型的计算系统

那么计算系统，有加减乘除取模等等方法，那么通过方法来构建最基本的算法

```java
public static double add(double a,double b) {
		double sum = a+b;
		return sum;
	}
	
	public static double sub(double a,double b) {
		double sub = a-b;
		return sub;
	}
	
	public static double mul(double a,double b) {
		double mul = a*b;
		return mul;
	}
	
	public static double div(double a , double b) {
		double div = a/b;
		return div;
	}
	public static double mod(double a, double b) {
		double mod = a%b;
		return mod;
	}
    ```

构建完成了基本的算法。

同样要写main中的内容，那么首先使用户交互的基本部分，但是因为引入了mod与除法所以要保证b不能是零（在main中也就是num2，在main中会把num2传参传入2中）

所以在基本的用户交互之上，需要try-catch的帮助（如果num2是零，抛出ArithmeticException 这个异常）

所以在上一题的基础上，需要搭建try-catch的语句，那么同样，可以引入inputmismatchexception这个异常，因为可能用户输入w等等这样的字母，为了防止代码崩溃，再引入这个异常。

同样如果num2==0的话，直接退出整个系统。

```java
Scanner input = new Scanner(System.in);
		try{
			System.out.println("你想要输入的第一个数字是 ");
			double num1 = input.nextDouble();
			System.out.println("你想要输入的第二个数字是  这个数字不能是零！！！");
			double num2 = input.nextDouble();
			if(num2==0) {
				System.out.println("不能是零！！");
                return;
			}

            }catch(ArithmeticException e) {
			System.out.println("num2 不能是零");
		}catch(InputMismatchException e) {
			System.out.println("输入错误，不能随便输入");
		}catch(Exception e) {
			System.out.println("错误！！ " + e.getMessage());
		}
```
这个是基本的用户交互的内容。

但是用户交互没有完，基本的完成了 但是用户不知道执行什么命令，所以需要他们来选择，这个使用do-while来制造菜单，然后通过switch-case-default语句来执行对应的选择。

首先初始化choice，
```java
// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		try{
			System.out.println("你想要输入的第一个数字是 ");
			double num1 = input.nextDouble();
			System.out.println("你想要输入的第二个数字是  这个数字不能是零！！！");
			double num2 = input.nextDouble();
			if(num2==0) {
				System.out.println("不能是零！！");
                return;
			}
			int choice ;

```
在do-while外面初始化，不然如果卸载do-while里面的话，while中的语句不知道choice是啥，就会报错。

接着构造 do-while语句
```java

			do {
				System.out.println("1：想要两个数字相加的");
				System.out.println("2: 想要两个数字相减的");
				System.out.println("3: 想要两个数字相乘的");
				System.out.println("4: 想要两个数字相除的（除法不是mod）");
				System.out.println("5: 想要两个数字相除的（mod）");
				System.out.println("6：想要结束的");
				 
				choice = input.nextInt();
				
```
这是菜单与choice的输入语句。

接着就是使用switch-case-default语句来执行代码，（不要忘记break！！！）
```java
do {
				System.out.println("1：想要两个数字相加的");
				System.out.println("2: 想要两个数字相减的");
				System.out.println("3: 想要两个数字相乘的");
				System.out.println("4: 想要两个数字相除的（除法不是mod）");
				System.out.println("5: 想要两个数字相除的（mod）");
				System.out.println("6：想要结束的");
				 
				choice = input.nextInt();
				
				switch(choice) {
				case 1:
					System.out.println("两个数字的和是 "+add(num1,num2));
					break;
					
				case 2:
					System.out.println("两个数字的差是 " + sub(num1,num2));
					break;
				
				case 3:
					System.out.println("两个数字的积是 " + mul(num1,num2));
					break;
				
				case 4:
					System.out.println("两个数字的商是 " + div(num1,num2));
					break;
					
				case 5:
					System.out.println("两个书的余数是 " + mod(num1,num2));
					break;
					
				case 6:
					System.out.println("谢谢");
					break;
				}
			}while(choice != 6);
```
这个就是基本的，一个菜单，然后让用户选择，选择完成后，进入方法执行命令，最后输出。

到这里，基本上已经把框架搭好了，但是仍然不好，如果用户想要直到num1-num2，显然num2可以是零，所以最后改过来的代码是
```java
import java.util.InputMismatchException;
import java.util.Scanner;
public class d {
	
	public static double add(double a,double b) {
		double sum = a+b;
		return sum;
	}
	
	public static double sub(double a,double b) {
		double sub = a-b;
		return sub;
	}
	
	public static double mul(double a,double b) {
		double mul = a*b;
		return mul;
	}
	
	public static double div(double a , double b) {
		double div = a/b;
		return div;
	}
	public static double mod(double a, double b) {
		double mod = a%b;
		return mod;
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		try{
			System.out.println("你想要输入的第一个数字是 ");
			double num1 = input.nextDouble();
			System.out.println("你想要输入的第二个数字是  这个数字不能是零！！！");
			double num2 = input.nextDouble();
			int choice ;

			do {
				System.out.println("1：想要两个数字相加的");
				System.out.println("2: 想要两个数字相减的");
				System.out.println("3: 想要两个数字相乘的");
				System.out.println("4: 想要两个数字相除的（除法不是mod）");
				System.out.println("5: 想要两个数字相除的（mod）");
				System.out.println("6：想要结束的");
				 
				choice = input.nextInt();
				
				switch(choice) {
				case 1:
					System.out.println("两个数字的和是 "+add(num1,num2));
					break;
					
				case 2:
					System.out.println("两个数字的差是 " + sub(num1,num2));
					break;
				
				case 3:
					System.out.println("两个数字的积是 " + mul(num1,num2));
					break;
				
				case 4:
					if(num2==0) {
						System.out.println("不能是零！！");
						return;
						
					}
					System.out.println("两个数字的商是 " + div(num1,num2));
					break;
					
				case 5:
					if(num2==0) {
						System.out.println("不能是零！！");
						return;
						
					}
					System.out.println("两个书的余数是 " + mod(num1,num2));
					break;
					
				case 6:
					System.out.println("谢谢");
					break;
				}
			}while(choice != 6);
			

			
		}catch(ArithmeticException e) {
			System.out.println("num2 不能是零");
		}catch(InputMismatchException e) {
			System.out.println("输入错误，不能随便输入");
		}catch(Exception e) {
			System.out.println("错误！！ " + e.getMessage());
		}
		

	}

}

```
这个就是最后的代码。
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/ace08ca7b42e4ec690467726d381a45e.png" width="600"/>
</p>

如果num2是0但是不是除法的情况呢
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/cfeb88da40474049891fd830cbd44c8d.png" width="600"/>
</p>

如果是除法的情况呢
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/1c4047a2fc7046a1aeabef6d9b7088d7.png" width="600"/>
</p>

循环直接停止了。

那么如果这个静态方法是boolean值呢？来看看对应的代码，如果要比较两个数字，那么在方法中，对应返回的是true或者false，所以要是用boolean值来进行。

所以需要构建一个boolean的方法，并且在main中写用户交互，然后传入参数，最后使用条件语句，进行分类讨论。

```java
import java.util.Scanner;
public class e {
	public static boolean compare(double a, double b) {
		if(a<b) {
			return true;
		}else {
			return false;
		}
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner input = new Scanner(System.in);
		System.out.println("第一个数字是 ");
		double num1 = input.nextDouble();
		System.out.println("第二个数字是 ");
		double num2 = input.nextDouble();
		
		if(compare(num1,num2)) {
			System.out.println("第一个数字比第二个数字大");
		}else{
			System.out.println("第二个数字大于等于第一个数字");
		}

	}

}
```
如果是使用void 没有任何返回方法的呢？一般是传回来一句话，同样可以直接打印，不需要使用return。
```java
public class f {
	public static void hello() {
		System.out.println("hello world, and hello java");
	}

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		hello();

	}

}

```
在方法中使用了void，说明方法返回没有数据类型，在这种类型下，不需要使用return，可以直接使用system.out.println输出，同样在main中可以直接调用。

这里输出
​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/21ca9ae018d64f92ac74a7a5c7166f20.png" width="600"/>
</p>
