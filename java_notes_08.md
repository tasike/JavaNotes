# JAVA NOTES（Part 8）==by tasike==

# 数组

- ## 数组介绍

- ## 数组的定义与静态初始化

- ## 数组元素访问

- ## 数组遍历

- ## 数组动态初始化

- ## 数组内存图

- ## 练习

---------------

## 1 数组介绍

可以向下兼容。
int类型的数组可以存储byte、short、int
double类型的数组可以存储byte、short、int、long、float、int

## 2 数组的定义与静态初始化

**静态初始化格式(简写)：**==静态初始化之后，数组的大小就固定了！==

```java
数据类型[] 数组名 = {元素1,元素2,元素3,...};
//实际上标准的格式还要在{}前面加上new 数据类型[]
int[] array = {1,2,3,4,5};
```

**数组的地址值：**

``` java
public class Test{
    public static void main(String[] args){
        int[] arr1 = {1,2,3,4,5};
        System.out.println(arr1);
    }
}
```

```
输出结果为：
[I@28a418fc
```

```
解释一下结果：
[:表示这是一个数组
I:表示是int类型
@:表示一个间隔符号(固定格式)
28a418fc:才是数组真正的地址值(十六进制)
```

## 3 数组元素访问(和c语言一样)

```java
public class Test{
    public static void main(String[] args){
        int[] arr1 = {1,2,3,4,5};
        System.out.println(arr1[0]);
    }
}
```

```
输出结果为：
1
```

**数组元素修改：**

```java
public class Test{
    public static void main(String[] args){
        int[] arr1 = {1,2,3,4,5};
        arr1[0] = 100;
        System.out.println(arr1[0]);
    }
}
```

```
输出结果：
100
```

## 4 数组遍历

**.length的使用可以获取数组的长度：**

```java
public class Test{
    public static void main(String[] args){
        int arr1 = {1,2,3,4,5,8,9,4,5,7,6,5,1,2,5,4,6,7,9,2,2,5,1,4,3};
        for(int i = 0; i < arr1.length; i++){
            System.out.println(arr1[i]);
        }
    }    
}
```

## 5 数组动态初始化

**格式：**

```java
数据类型[] 数组名 = new 数据类型[数组的长度];
int[] arr = new int[10]; //指初始化了一个长度为10的数组,其内元素的初始化值由虚拟机给出
```

**动态初始化数组的元素的默认初始化值规律：**

```
整数类型，默认初始化值为0
小数类型，默认初始化值为0.0
字符(char)类型，默认初始化值为'\u0000',就是空格
布尔类型，默认初始化值为False
引用数据类型(String等等)，默认初始值为null
```

案例：
```java
public class Test{
    public static void main(String[] args){
        int[] arr1 = new int[10];
        double[] arr2 = new double[10];
        char[] arr3 = new char[10];
        boolean[] arr4 = new boolean[10];
        String[] arr5 = new String[10];

        System.out.println(arr1[0]);
        System.out.println(arr2[0]);
        System.out.println(arr3[0]);
        System.out.println(arr4[0]);
        System.out.println(arr5[0]);
    }    
}
```

```
输出结果为：
0
0.0

false
null
```

## 6 数组内存图

- ### java内存分配

  - **栈**：方法运行时使用的内存，比如main方法运行，进入方法栈中执行

    程序的主入口(main方法)在开始执行时进栈，执行完毕后出栈

  - **堆**：存储对象或者数组，new来创建的，都存储在堆内存

    new出来的东西会在堆内存中开辟空间并产生地址

  - **方法区**：存储可以运行的class文件

  - **本地方法栈**：JVM在使用操作系统功能的时候使用，与开发无关

  - **寄存器**：给CPU使用，与开发无关

  **java也存在数组浅拷贝的情况：**

  ```java
  public class Test{
      public static void main(String[] args){
          int[] arr1 = {11,22};
          int[] arr2 = arr1;
          arr2[0] = 33;
          System.out.println(arr2[0]);
          System.out.println(arr1[0]);
      }    
  }
  ```

  ```
  输出结果为：
  33
  33
  ```


## 7 练习

练习1：已知数组为{33，2，55，44，22}，写一段程序得到最值并打印出来
```java
public class Test{
    public static void main(String[] args){
        int[] arr = {33,2,55,44,22};
        int min = arr[0];
        int max = arr[0];
        for(int i = 1; i < arr.length; i++){
            min = min < arr[i] ? min : arr[i];
            max = max > arr[i] ? max : arr[i];
        }
        System.out.println("最小值为：" + min);
        System.out.println("最大值为：" + max);
    }    
}
```

练习2：生成10个1~100的随机数存入数组中，1）求出所有数据的和。2）求所有数据的平均数。3）统计有多少个数据比平均数小
```java
import java.util.Random;

public class Test{
    public static void main(String[] args){
        Random r = new Random();
        int[] arr = new int[10];
        int sum = 0;
        for(int i = 0; i < arr.length; i++){
            arr[i] = r.nextInt(1,101);
            sum += arr[i];
        }
        double average = sum / 10.0;
        int count = 0;
        for(int i = 0; i < arr.length; i++){
            if(arr[i] < average){
                count++;
            }
        }
        System.out.println("所有数据的和为：" + sum);
        System.out.println("所有数据的平均数为：" + average);
        System.out.println("比平均数小的数据个数为：" + count);
    }    
}
```

==小知识：System.out.print可以在同一行输出而不换行==

练习3：定义一个数组，存入1，2，3，4，5，交换首尾的数据。
```java
public class Test{
    public static void main(String[] args){
        int[] arr = {1,2,3,4,5};
        int temp = arr[0];
        arr[0] = arr[4];
        arr[4] = temp;
        System.out.print("首尾交换后的数组为：");
        for(int i = 0; i < 5; i++){
            System.out.print(arr[i] + " ");
        }
    }    
}
```

练习4：定义一个数组，存入1，2，3，4，5，打乱数组中所有数据的顺序。
```java
import java.util.Random;

public class Test{
    public static void main(String[] args){
        int[] arr = {1,2,3,4,5};
        Random r = new Random();
        for(int i = 0; i < arr.length; i++){
            int j = r.nextInt(5);
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
        System.out.print("打乱后的数组为：");
        for(int i = 0; i < arr.length; i++){
            System.out.print(arr[i] + " ");
        }
    }    
}
```























