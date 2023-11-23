# JAVA NOTES（Part 3）==by tasike==

- ## 数据类型

- ## 标识符

- ## 键盘录入

--------------------

> ## 数据类型

- 数据类型的分类
  - 基本数据类型
  
    - | 数据类型 | 关键字  |                    取值范围                    | 占用字节 |
      | :------: | :-----: | :--------------------------------------------: | :------: |
      |    整    |  byte   |                    -128~127                    |    1     |
      |    数    |  short  |                  -32768~32767                  |    2     |
      |    类    |   int   |          -2147483648~2147483647(10位)          |    4     |
      |    型    |  long   | -9223372036854775808~9223372036854775807(19位) |    8     |
      |   浮点   |  float  |           -3.401298e-38~3.402823e+38           |    4     |
      |   类型   | double  |         -4.9000000e-324~1.797693e+308          |    8     |
      | 字符类型 |  char   |                    0~65535                     |    2     |
      | 布尔类型 | boolean |                   true,false                   |    1     |
  
      > **取值范围：double > float > long > int > short > byte**
  
      ```java
      public class demo4{
          //主入口
          public static void main(String[] args){
              //byte
              byte b = 24;
              System.out.println(b);
              
              //short
              short s = 906;
              System.out.println(s);
              
              //int
              int i = 20031227;
              System.out.println(i);
              
              //long
              //如果要定义long类型的变量
              //在数据值的后面需要加一个L作为后缀
              //L可以是大写的，也可以是小写的，但是最好是大写的，因为小写的容易混淆
              long n = 9999999999L;
              System.out.println(n);
              
              //float
              //和long同理，需要后缀，它的后缀是F
              float f = 2003.12F;
              System.out.println(f);
              
              //double,不需要后缀
              double d = 12.27;
              System.out.println(d);
              
              //char
              char c = 'a';
              System.out.println(c);
              
              //boolean
              boolean tr = true;
              boolean fal = false;
              System.out.println(tr);
              System.out.println(fal);
          }
      }
      ```
  
      
  
  - 引用数据类型
  
    - 类
    - 接口
    - 数组

> ## 标识符（指给类，方法，变量等起的名字）

1. 命名规则（硬性约束）
   - 由数字、字母、下划线、美元符($)组成
   - 不能以数字开头
   - 不能用关键字
   - 区分大小写

2. 命名规则（软性建议）

   1. > 对于方法和变量：
      >
      > - 规范1：标识符是一个单词的时候，全部小写
      > - 规范2：标识符由多个单词组成的时候，第一个单词首字母小写，其他单词首字母大写

   2. > 对于类：
      >
      > - 规范1：标识符是一个单词的时候，首字母大写
      > - 规范2：标识符由多个单词组成的时候，每个单词的首字母大写

> ## 键盘录入

```java
//1.导包，找到Scanner这个类的位置
import java.util.Scanner;

public class ScannerTest{
    public static void main(String[] args){
        //2.创建对象，表示准备用Scanner这个类
        Scanner sc = new Scanner(System.in);
        
        System.out.println("请输入一个整数：");
        
        //3.接受数据，并把数据保存在变量i中
        int i = sc.nextInt();
        System.out.println(i);
    }
}
```

练习：键盘输入2个数字，输出相加的结果

```java
//在vscode里安装自动导包插件之后，就不用自己导包了，只要如下面的第6行输入Sc再按回车就自动导包了
import java.util.Scanner;

public class Sum{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        System.out.println("请输入第一个数字：");
        int number1 = sc.nextInt();
        
        System.out.println("请输入第二个数字：");
        int number2 = sc.nextInt();
        
        System.out.println("相加的结果是：");
        System.out.println(number1 + number2);
    }
}
```







