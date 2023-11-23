# JAVA NOTES（Part 4）==by tasike==

- ## 算术运算符

- ## 自增自减运算符

- ## 赋值运算符

- ## 比较运算符

- ## 逻辑运算符

- ## 三元运算符

- ## 运算符优先级

-----

### 一、算术运算符（和c语言相同）

| 符号 | 作用 |
| :--- | :--- |
| +    | 加   |
| -    | 减   |
| *    | 乘   |
| /    | 除   |
| %    | 取模 |

1. 在计算小数相加的时候有时候会出现精度错误

```java
public class Arithmetic1{

    public static void main(String[] args){

        System.out.println(1.1 + 1.1);

        System.out.println(1.1 + 1.01);

    }

}
```

> 输出结果
>
> > 2.2
> > 2.1100000000000003

2. 练习：键盘录入一个四位数，输出该三位数的个位、十位、百位、千位

```java
import java.util.Scanner;

public class Arithmetic2{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个四位数：");
        int i = sc.nextInt();
        
        // %10相当于取末位
        System.out.println(i % 10);
        
        // /10相当于去末位
        System.out.println(i / 10 % 10);
        
        // /100相当于去后两位
        System.out.println(i / 100 % 10);
        
        // /1000相当于去后三位
        System.out.println(i / 1000);
    }
}
```

- **自动类型提升：< int 的和 int 计算 ，< int的自动提升为int**

  ​							**int 和 > int 计算，int自动提升为 > int的**

  ​							**< int 和 > int 计算，< int 自动提升为 > int的**

  ​							**< int 和 < int 计算，都提升为 int **

- **强制类型提升：（目标数据类型）被强制转化的数据**

### **3.+ 不仅可以作为运算符，还可以作为连接符：字符串连接符和字符连接符**

> 当+操作符的操作对象中包含字符串时，+变为字符串连接符，并且遵循==从左到右==
>
> "123" + 123  ==>   "123123"
> 1 + 99 +"年小黑子"  ==> "100年小黑子"
> 1 + 2 + "abc" + 2 + 1  ==>  "3abc21"

练习：上一个练习的改进，输出的时候要求输出：个位是：，十位是，百位是，千位是

```java
import java.util.Scanner;

public class Arithmetic3{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入一个四位数：");
        int i = sc.nextInt();
        System.out.println("个位是：" + i % 10);
        System.out.println("十位是：" + i / 10 % 10);
        System.out.println("百位是：" + i / 100 % 10);
        System.out.println("千位是：" + i / 1000);
    }
}
```

> 字符+字符，或者字符+数字，会通过ASCII对应的数字进行运算
>
> 1 + 'a' ==> 98
> 'a' + "abc" ==> "aabc"

---------------------

### 二、自增自减运算符

- **++**

  - 作为后缀时，先用后加
  - 作为前缀时，先加后用

  ```java
  public class Tset{
      public static void main(String[] args){
          int a = 10;
          int b = 10;
          int c = a++;
          int d = ++b;
          System.out.println(c);
          System.out.println(d);
      }
  }
  ```

  > 运行结果：
  > 10
  > 11

  ```java
  public class Test{
      public static void main(String[] args){
          int x = 10;
          int y = x++;
          int z = ++x;
          System.out.println("x:" + x);
          System.out.println("y:" + y);
          System.out.println("z:" + z);
      }
  }
  ```

  > 运行结果：
  > 12
  > 10
  > 12

- **--**

----------------

### 三、赋值运算符

**包括=，+=，-=，*=，/=，%=**
==细节：+=，-=，*=，/=，%=底层都隐藏了一个强制类型转化：==

> short a = 1;
> a += 1;    ====>==     ==此处实际上相当于a = (short)(a + 1);==

----------------------

### 四、比较运算符

包括==,!=,>,>=,<,<=

练习：您马上要约会了，键盘录入两个整数，分别表示你的衣服时髦程度和你约会对象的衣服时髦程度(1~10)；如果您的衣服时髦程度大于等于你约会对象的时髦程度，输出true，否则输出false。

```java
import java.util.Scanner;

public class DateFashion{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入您的衣服时髦程度：");
        int boyFashion = sc.nextInt();
        System.out.println("请输入您约会对象的衣服时髦程度：");
        int girlFashion = sc.nextInt();
        System.out.println(boyFashion >= girlFashion);
    }
}
```

--------------

### 五、逻辑运算符

| 符号 |   作用   |          说明           |
| :--: | :------: | :---------------------: |
|  &   |  逻辑与  |        字面意思         |
|  \|  |  逻辑或  |        字面意思         |
|  ^   | 逻辑异或 | 相同为false，不同为true |
|  !   |  逻辑非  |        字面意思         |

#### ==短路逻辑运算符==

| 符号 |  作用  |                  说明                  |
| :--: | :----: | :------------------------------------: |
|  &&  | 短路与 | 结果和&相同，但是效率更高(有短路效果)  |
| \|\| | 短路或 | 结果和\|相同，但是效率更高(有短路效果) |

> ==短路效果：指的是当左边的表达式能确定最终结果时，右边的表达式就不参与运算了，因此效果更高==
>
> ==下面演示一下==
>
> ```java
> public class Test{
>     public static void main(String[] args){
>         int a = 10;
>         int b = 10;
>         boolean c = ++a < 5 && ++b < 5;
>         System.out.println(c);
>         System.out.println(a);
>         System.out.println(b);
>     }
> }
> ```
>
> ==运行结果：==
>
> ==false==
> ==11==
> ==10== ==说明b没有参与运算==
>
> ==而上面的代码中，如果把&&换成&，那么b会变成11==

练习：键盘录入两个整数，如果其中一个为6，输出true；如果两个数字的和为6的倍数，输出true；其他情况输出false
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入第一个整数：");
        int number1 = sc.nextInt();
        System.out.println("请输入第二个整数：");
        int number2 = sc.nextInt();
        boolean result = (number1 == 6 || number2 == 6)||((number1 + number2) % 6 == 0);
        System.out.println(result);
    }
}
```

-------------------

### 六、三元运算符

#### ==**格式**==

#### ==**关系表达式?表达式1:表达式2           注意：三元运算符的结果必须使用**==

练习：键盘录入两个整数，输出较大的那个（输出形式：较大的是：）
```java
import java.util.Scanner;

public class Max{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入第一个整数：");
        int number1 = sc.nextInt();
        System.out.println("请输入第二个整数：");
        int number2 = sc.nextInt();
        System.out.println(number1 >= number2 ? ("较大的是" + number1) : ("较大的是" + number2));
    }
}
```

练习：键盘录入三个整数，输出最大的那个
```java
import java.util.Scanner;

public class Max{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入第一个整数：");
        int number1 = sc.nextInt();
        System.out.println("请输入第二个整数：");
        int number2 = sc.nextInt();
        System.out.println("请输入第三个整数：");
        int number3 = sc.nextInt();
        int temp = number1 > number2 ? number1 : number2;
        int max = temp > number3 ? temp : number3;
        System.out.println("最大的数字是：" + max);
    }
}
```

---------------

### 七、运算符优先级

| 优先级（越小越优先） | 运算符                    |
| -------------------- | ------------------------- |
| 1                    | .  ()  {}                 |
| 2                    | !、~、++、--              |
| 3                    | *、/、%                   |
| 4                    | +、-                      |
| 5                    | <<、>>、>>>               |
| 6                    | <、<=、>、>=、instanceof  |
| 7                    | ==、!=                    |
| 8                    | &                         |
| 9                    | ^                         |
| 10                   | \|                        |
| 11                   | &&                        |
| 12                   | \|\|                      |
| 13                   | ?:                        |
| 14                   | =、+=、-=、*=、/=、%=、&= |











