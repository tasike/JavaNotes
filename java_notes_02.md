# JAVA NOTES（Part 2）==by tasike==

- ## 注释

- ## 关键字

- ## 字面量

- ## 变量

- ## 整理代码快捷键

----

### 01注释 ==快捷键：Ctrl+/==

#### 			1.1注释分类

- 单行注释 

  > // 注释信息

- 多行注释

  > /* 注释信息 */

- 文档注释

  > /** 注释信息 */

--------

### 02关键字

#### 	2.1class

``` java
public class helloworld{
    
    
}
```

- ##### class用于 创建/定义 一个类，类是JAVA中最基本的组成单元

- ##### helloworld是这个类的名字

-------

### 03字面量

#### 	3.1字面量的分类

- ##### 整数类型

- ##### 小数类型

- ##### 字符串类型

  > "字符串"

- ##### 字符类型

  > '字符'，单引号里面只能有一个

- ##### 布尔类型

  > 只有两个值：true和false

- ##### 空类型

  > 值是：null

  ```java
  public class demo1{
      //下面这行在vscode里直接敲psvm再回车就会出来
      public static void main(String[] args){
          //下面这行在vscode里直接敲sout再回车就会出来
          System.out.println(666);
          System.out.println(13.14);
          System.out.println("我是tasike");
          System.out.println('男');
          System.out.println(true);
          System.out.println(false);
          // null不能直接打印，真要打就要把它用字符串打出来
      }
  }
  ```

#### 	3.2特殊字符

- ##### \t 制表符

  > 在打印的时候，把前面字符串的长度补齐到8或者8的整倍数。最少补一个空格，最多补8个空格。

  ``` java
  public class demo2{
      public static void main(String[] args){
          System.out.println("name" + '\t' + "age");
          System.out.println("tasike" + '\t' + "19");
      }
  }
  ```

  > 运行结果：
  >
  > name		age
  >
  > tasike		19

---------

### 04变量

#### 	4.1变量的定义

> java中变量的定义和c语言相同

```java
public class demo3{
    public static void main(String[] args){
        int a = 15;
        System.out.println(a);
        double b = 3.14159;
        System.out.println(b);
        System.out.println(a + b);
        a = 20;
        System.out.println(a);
        int c = 100,d = 200,e = 300;
        System.out.println(c);
        System.out.println(d);
        System.out.println(e);
    }
}
```

> 运行结果：
>
> 15
>
> 3.14159
>
> 18.14159
>
> 20
>
> 100
>
> 200
>
> 300

##### 注：+= 也是可以使用的，++也是可以使用的

-----------------

### 05整理代码快捷键

```java
Shift + Alt + F : 快速整理代码
```

