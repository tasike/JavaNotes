# JAVA NOTES（Part 7）==by tasike==

# 循环高级

- ## 无限循环

- ## 跳转控制语句

- ## 练习

------------

## 一、无限循环

```java
第一种
do{
    System.out.println("学习");
}while(true);


第二种
for(;;){
    System.out.println("学习");
}


第三种
while(true){
    System.out.println("学习");
}
```

==想要终止无限循环，按ctrl + c即可==

---------------

## 二、跳转控制语句

```java
第一种
continue  跳过本次循环，继续下次循环
    
第二种
break    结束整个循环(一层)
```

--------------

## 三、练习

练习1：在控制台打印出从1到10000中包含7以及是7的倍数的数据

```java
public class Test1{
    public static void main(String[] args){
        for(int i = 1; i <= 10000; i++){
            int temp = i;
            if(temp % 7 == 0){
                System.out.println(i);
            }else{
                while(temp > 0){
                    if(temp % 10 == 7){
                        System.out.println(i);
                        break;
                    }
                    temp /= 10;
                }
            }
        }
    }
}
```

练习2：键盘录入一个大于等于2的整数，输出其算数平方根，结果只保留整数部分
```java
import java.util.Scanner;

public class Test2{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个大于等于2的整数：");
        int integer = sc.nextInt();
        for(int i = 1; i <= integer; i++){
            if(i * i > integer){
                System.out.println(i-1);
                break;
            }
        }
    }
}
```

练习3：键盘录入一个正整数，判断是否是质数，是的话输出true，不是的话输出false
```java
import java.util.Scanner;

public class Test3{
    public static void main(String[] args){
        int flag = 0;
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个正整数：");
        int integer = sc.nextInt();
        if(integer == 1){
            System.out.println("false");
        }else if(integer == 2){
            System.out.println("true");
        }else{
            for(int i = 2; i <= integer/2; i++){
                if(integer % i == 0){
                    flag = 1;
                    System.out.println("false");
                    break;
                }
            }
            if(flag == 0){
                System.out.println("true");
            }
        }
    }
}
```

改进版本(还未改到最佳)
```java
import java.util.Scanner;

public class Test3{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个正整数：");
        int integer = sc.nextInt();
        if(integer == 1){
            System.out.println("false");
            return;
        }
        
        boolean flag = true;
        for(int i = 2; i < integer; i++){
            if(integer % i == 0){
                flag = false;
                break;
            }
        }
        System.out.println(flag);
    }
}
```

练习4：程序自动生成一个1~100的随机数字，使用程序实现猜出这个数字是多少
```java
import java.util.Random;
import java.util.Scanner;

public class Test{
    public static void main(String[] args) {
        Random r = new Random(); //按Ran回车就可以实现自动导包(即第一行的导包)
        int integer = r.nextInt(1,101);
        Scanner sc = new Scanner(System.in);
        boolean flag = true;
        while(flag){
            System.out.println("请输入你要猜的数字：");
            int guess = sc.nextInt();
            if(guess < integer){
                System.out.println("小了");
            }else if(guess > integer){
                System.out.println("大了");
            }else{
                System.out.println("恭喜你猜对了");
                flag = false;
            }
        }    
    }
}
```

再加一个保底机制，猜5次必中
```java
import java.util.Random;
import java.util.Scanner;

public class Test{
    public static void main(String[] args) {
        Random r = new Random();
        int integer = r.nextInt(1,101);
        Scanner sc = new Scanner(System.in);
        int count = 0;
        boolean flag = true;
        while(flag){
            System.out.println("请输入你要猜的数字：");
            int guess = sc.nextInt();
            count++;
            if(count == 5){
                System.out.println("恭喜你猜对了");
                break;
            }
            if(guess < integer){
                System.out.println("小了");
            }else if(guess > integer){
                System.out.println("大了");
            }else{
                System.out.println("恭喜你猜对了");
                flag = false;
            }
        }    
    }
}
```

