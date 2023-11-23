# JAVA NOTES（Part 12）==by tasike==

# 二维数组

## 1 二维数组的静态初始化

**格式：**

```java
数据类型[][] 数组名 = {{元素1,元素2,...},{元素1,元素2,....},.....};
```

**建议格式：**

```java
数据类型[][] 数组名 = {
    {元素1,元素2,...},
    {元素1,元素2,....},
    .....
};
```

**案例：**

```java
int[][] arr = {
    {1,2,3},
    {4,5,6,7,8},
    {9,10}
};
```

**获取元素：**

```java
public class Test{
    public static void main(String[] args){
        int[][] arr = {
            {1,2,3},
            {4,5,6,7,8},
            {9,10}
        };
        System.out.println(arr[0]);  //这里获取的其实是地址值
        System.out.println(arr[0][0]);
    }
}
```

```
输出结果为：
[I@28a418fc
1
```

**遍历数组元素：**

```java
public class Test{
    public static void main(String[] args){
        int[][] arr = {
            {1,2,3},
            {4,5,6,7,8},
            {9,10}
        };
        for(int i = 0; i < arr.length; i++){
            for(int j = 0; j < arr[i].length; j++){
                System.out.print(arr[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

```
输出结果为：
1 2 3 
4 5 6 7 8
9 10
```

--------------------

## 2 二维数组的动态初始化

**格式：**

```java
数据类型[][] arr = new 数据类型[m][n];
```

**案例：**

```java
int[][] arr = new int[3][2];
```

==但是这样写，使得二维数组中的一维数组的长度都是一样的。为了灵活地使得一维数组的长度可以不固定，可以如下写法：==

```java
int[][] arr = new int[3][];
int[] arr1 = {1,2,3};
int[] arr2 = {4,5,6,7,8};
int[] arr3 = {9,10};
arr[0] = arr1;
arr[1] = arr2;
arr[2] = arr3;
```

