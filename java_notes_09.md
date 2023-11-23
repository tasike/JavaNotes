# JAVA NOTES（Part 9）==by tasike==

# 方法

- ## 什么是方法？

- ## 方法的格式

- ## 方法的重载


-------------

## 1 什么是方法

==方法是程序中最小的执行单元==
比如下面这两段都是方法：

```java
public static void main(String[] args){
    // 这是主方法
}

public static void method(){
    
}
```

==方法其实就是类似c语言的函数，比如c语言的main是主函数==

## 2 方法的格式

```java
public static 返回值类型 方法名(参数1,参数2,....){
    方法体;
    return 返回值;
}
```

演示一下书写playGame方法的定义和调用：
```java
public class Test{
    public static void main(String[] args){
        playGame();
    }
    public static void playGame(){
        System.out.println("选人物");
        System.out.println("准备开局");
        System.out.println("对线");
        System.out.println("坐牢");
        System.out.println("崩盘");
        System.out.println("骂队友");
        System.out.println("送人头");
        System.out.println("GG");
    }    
}
```

```
输出结果为：
选人物
准备开局
对线
坐牢
崩盘
骂队友
送人头
GG
```

**练习1：写一个方法，使得调用该方法可以实现展示==女朋友==的所有信息。**

```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        girlFriend();
    }
    public static void girlFriend(){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入您的姓名：");
        String name = sc.nextLine(); //键盘键入一个字符串
        boolean flag = false;
        if("李炜".equals(name)){    //比较两个字符串
            flag = true;
        }
        if(flag){
            System.out.println("下面将输出您的女朋友信息：");
            System.out.println("姓名：翁昕悦");
            System.out.println("性别：女");
            System.out.println("年龄：永远18");
            System.out.println("身高：一米八大长腿");
            System.out.println("身份：李炜的甜蜜女友");
            System.out.println("职业：女警");
            System.out.println("性格：温柔、孝顺、体贴、善解人意、贤惠");
            System.out.println("颜值：天仙下凡，可爱动人，笑容倾城");
        }else{
            System.out.println("抱歉，您目前还没有女朋友呢");
        }
    }    
}
```

```
就不演示输出结果了，哇哈哈哈哈哈哈哈哈哈哈哈
```

练习2：写一个求和方法，使得每次输入两个整数可以得到其和：
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入第一个加数(整数)：");
        int a = sc.nextInt();
        System.out.println("请输入第二个加数(整数)：");
        int b = sc.nextInt();
        System.out.println("这两个数字的和为：" + getSum(a, b));
    }
    public static int getSum(int num1, int num2){
        return num1 + num2;
    }    
}
```

## 3 方法的重载

**就是在同一个类中，方法名一样，但是形参不同(形参个数不同，类型不同)，那么这些方法就构成重载关系**

练习1：使用方法重载的思想，设计比较两个整数是否相等的方法（只需写出方法即可）。要求：兼容全整数类型(byte,short,int,long)
```java
public static void compare(byte b1, byte b2){
	System.out.println(b1 == b2);
}
public static void compare(short s1, short s2){
	System.out.println(s1 == s2);
}    
public static void compare(int i1, int i2){
	System.out.println(i1 == i2);
}
public static void compare(long n1, long n2){
	System.out.println(n1 == n2);
}
```

练习2：设计一个方法用于数组遍历，数组为{1, 2, 3, 4, 5},要求遍历后输出的结果在一行上([1，2，3，4，5])
```java
public class Test{
    public static void main(String[] args){
        int[] arr = {1,2,3,4,5};
        printArr(arr);
    }
    public static void printArr(int[] arr){
        System.out.print("[");
        for(int i = 0; i < arr.length; i++){
            if(i == arr.length - 1){
                System.out.print(arr[i] + "]");
            }else{
                System.out.print(arr[i] + ", ");
            }
        }
    }
}
```

```
输出结果为：
[1, 2, 3, 4, 5]
```

练习3：定义一个方法copyOfRange(int[] arr, int from, int to)，功能是将数组arr中从索引from开始(包括from)到索引to(不包括to)的元素复制到新数组中，并把新数组返回
```java
	public static int[] copyOfRange(int[] arr, int from, int to){
        int[] brr = new int[to - from];
        for(int i = from; i < to; i++){
            brr[i - from] = arr[i];
        }
        return brr;
    }
```

