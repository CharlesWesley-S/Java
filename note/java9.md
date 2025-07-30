# 9：java学习笔记：do-while语句
do-while也是一种循环语句，与while很像，但是与while刚刚好反一下。

## 9.1 do-while的基本结构
```java
do {
    // 循环体：要执行的代码
} while (条件);
```
do--while是先循环，再判断条件，就是先执行代码，然后呢判断条件，

循环体先执行一次；

然后判断条件；

如果条件为 true，再重复执行；

如果条件为 false，就退出。

这个结构刚刚好和while循环的结构是相反的。

注意！！while(条件）最后一定要加;，不要忘记了。

## 9.2do-while例子
那么看一下例子

```java

import java.util.Scanner;

public class e2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int number;

        do {
            System.out.print("请输入一个正整数：");
            number = input.nextInt();
        } while (number <= 0);

        System.out.println("你输入了：" + number);
    }
}
```
输入一个正数，比如这个，不管什么情况，第一次一定执行，然后来看这个while（条件）里面的条件，如果是true的话重复执行，如果false的话就退出。

来看一下

​<p align="center">
  <img src="https://i-blog.csdnimg.cn/direct/9cd3c93099cb4b768de6dd2e32a5cc84.png" width="600"/>
</p>

请输入一个正整数，第一个：-1while（条件）判断是true所以继续，同理，继续，到三后，判断出来是false，所以结束，然后打印出来。

do-while使用的情况比较少，比较与if条件语句，for循环语句，while循环语句，try-catch语句这些，使用频率非常低，不是没有用，只是用处太少了，因为大部分人还是喜欢使用while循环语句。一般使用菜单，比如说游戏中有一个列表让你选择，第一：继续游戏，第二：新游戏，第三：商店等等等等 同样学生系统也是这样的。

```java
import java.util.Scanner;

public class e2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int choice;

        do {
            System.out.println("\n==== 欢迎使用学生成绩系统 ====");
            System.out.println("1. 查询成绩");
            System.out.println("2. 修改成绩");
            System.out.println("3. 删除成绩");
            System.out.println("4. 退出系统");
            System.out.print("请输入你的选项（1-4）：");

            choice = input.nextInt();

            switch (choice) {
                case 1:
                    System.out.println("你选择了【查询成绩】功能");
                    break;
                case 2:
                    System.out.println("你选择了【修改成绩】功能");
                    break;
                case 3:
                    System.out.println("你选择了【删除成绩】功能");
                    break;
                case 4:
                    System.out.println("正在退出系统，感谢使用！");
                    break;
                default:
                    System.out.println("无效选项，请重新输入（1-4）");
            }
        } while (choice != 4);
    }
}
```
一开始使用do--while语句，然后呢，后面使用了switch-case-default语句，如果你选择的choice不是四，那么最后的while判断是true，那么继续上面的代码，如果是false的话，那么结束代码，这个就是菜单，常用do-while。