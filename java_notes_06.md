# JAVA NOTES（Part 6）==by tasike==

# 循环高级

# 流程控制语句

- ## 顺序结构

- ## 分支结构

- ## 循环结构

- ## 一些练习

-----------------------------

## 一、顺序结构

> 指代码按从上到下的顺序执行

------------------

## 二、分支结构

- ### if

- ### switch

### 1.if语句

- #### if的第一种格式

```java
if(关系表达式){
    语句体;
}
如果只有一个语;句，那么花括号可以省略。
    
要注意一个东西：int a = 100;这是两个语句(int a;和a = 100;)，因此当if的执行语句中有定义并且赋值变量时必须要花括号。
```

练习：老丈人测试女婿的酒量，键盘录入女婿的酒量，如果酒量大于10，输出“小伙子好样的”，否则不回应
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入小伙子的酒量：(整数)");
        int wine = sc.nextInt();
        if(wine > 10){
            System.out.println("小伙子好样的");
        }
    }
}
```

- #### if的第二种格式

```java
if(关系表达式){
    语句体1;
}else{
    语句体2;
}
```

- #### if的第三种格式

```java
if(关系表达式1){
    语句体1;
}else if(关系表达式2){
    语句体2;
}else if(关系表达式3){
    语句体3;
}....
.....
 else{
    语句体 n+1;
}
```

### 2.switch语句

```java
switch(表达式){
    case 值1:
        语句体1;
        break;
    case 值2:
        语句体2;
        break;
    case 值3:
        语句体3;
        break;
    .......
    default:
        语句体n+1;
        break;
}
```

==表达式和case后面的匹配值，取值为byte,short,int,char,String==

还有switch的新写法：

```java
switch(表达式){
        case 值1 -> {
            语句体1;
        }
        case 值2 -> {
            语句体2;
        }
        .........
        default -> {
            语句体n+1;
        }
}
```

练习：键盘录入星期数，输出工作日、休息日
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int week = sc.nextInt();
        switch(week){
            case 1,2,3,4,5 -> System.out.println("工作日");
            case 6,7 -> System.out.println("休息日");
            default -> System.out.println("没有这个星期");
        }
    }
}
```

--------------

## 三、循环结构

- ### do...while

- ### for

- ### while

### 1.do...while循环

```java
初始化语句;
do{
    循环体语句;
    条件控制语句;
}while(条件判断语句);
```



### 2.for循环(和c语言一模一样)

```java
for(初始化语句;条件判断语句;条件控制语句){
    循环体语句;
}
```

### 3.while循环(和c语言一模一样)

```java
初始化语句;
while(条件判断语句){
    循环体语句;
    条件控制语句;
}
```

==对于for循环和while循环的区别，一般来说，for循环知道循环的次数，用于遍历，而while循环则一般是不知道循环的次数，只知道循环结束的条件==



## 四、一些练习

==练习1：键盘录入一个正整数，判读是否为回文数，如果是输出true,如果不是输出false==

```java
import java.util.Scanner;

public class IsPalindromeNumber{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个正整数：");
        int number = sc.nextInt();
        int n = 0;
        int temp = number;
        while(temp > 0){
            int end_of_number = temp % 10;
            temp /= 10;
            n = n * 10 + end_of_number;
        }
        System.out.println(number == n);
    }
}
```

==练习2：键盘录入两个正整数，被除数和除数(不超过int范围)，要求不使用*，/，%得到它们的商和余数==

```java
import java.util.Scanner;

public class Division{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入被除数：");
        int dividend = sc.nextInt();
        System.out.println("请输入除数：");
        int divisor = sc.nextInt();
        int quotient = 0;
        int temp = dividend;
        while(temp >= divisor){
            temp -= divisor;
            quotient++;
        }
        System.out.println("商为" + quotient + ",余数为" + temp);
    }
}
```

