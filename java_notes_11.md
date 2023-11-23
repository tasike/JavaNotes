# JAVA NOTES（Part 11）==by tasike==

# 综合练习

练习1：卖飞机票。输入飞机原价、月份、头等舱或者经济舱。旺季(5-10月)头等舱9折，经济舱8.5折；淡季(11-4月)头等舱7折，经济舱6.5折。输出实际票价。
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入飞机票原价：");
        int price = sc.nextInt();
        boolean flag1 = true;
        boolean flag2 = true;
        int month = 0;
        while(flag1){
            if(flag2){
                System.out.println("请输入现在的月份：");
                flag2 = false;
            }
            month = sc.nextInt();
            if(month < 1 || month > 12){
                System.out.println("输入的月份不合法，请重新输入：");
            }else{
                flag1 = false;
                System.out.println(flag1);
                System.out.println(month);
            }
        }
        flag1 = true;
        flag2 = true;
        int choice = 0;
        while(flag1){
            if(flag2){
                System.out.println("选择头等舱或经济舱？0表示选择头等舱，1表示选择经济舱：");
                flag2 = false;
            }
            choice = sc.nextInt();
            if(choice != 0 && choice != 1){
                System.out.println("输入的选择不合法，请重新输入：");
            }else{
                flag1 = false;
            }
        }
        double newPrice;
        if(month >= 5 && month <= 10){
            if(choice == 0){
                newPrice = price * 0.9;
            }else{
                newPrice = price * 0.85; 
            }
        }else{
            if(choice == 0){
                newPrice = price * 0.7;
            }else{
                newPrice = price * 0.65;
            }
        }
        System.out.println("您实际应付的金额为：" + newPrice);
    }
}
```

练习2：统计101到200之间的质数个数，输出所有质数和个数。
```java
public class Test{
    public static void main(String[] args){
        int count = 0;
        for(int i = 101; i <= 200; i++){
            if(isPrime(i)){
                count++;
                System.out.print(i + " ");
            }
        }
        System.out.println();
        System.out.println("总个数为：" + count);
    }
    public static boolean isPrime(int number){
        if(number == 1){
            return false;
        }else if(number == 2){
            return true;
        }else{
            for(int i = 2; i < number / 2; i++){
                if(number % i == 0){
                    return false;
                }
            }
            return true;
        }
    }
}
```

练习3：定义方法实现随机产生一个5位的验证码，前四位是大写字母或小写字母，最后一位是数字。
```java
import java.util.Random;

public class Test{
    public static void main(String[] args){
        char[] str = new char[52];
        for(int i = 0; i < str.length; i++){
            if(i <= 25){
                str[i] = (char)(97 + i);
            }else{
                str[i] = (char)(65 + i - 26);
            }
        }
        Random r = new Random();
        String code = "";
        for(int i = 0; i < 4; i++){
            int index = r.nextInt(str.length);
            code = code + str[index];
        }
        int number = r.nextInt(10);
        code = code + number;
        System.out.println(code);
    }
}
```

练习4：把一个数组{1，2，3，4，5}复制到一个新的数组中。
```java
public class Test{
    public static void main(String[] args){
        int[] arr = {1,2,3,4,5};
        int[] newArr = new int[arr.length];
        for(int i = 0; i < arr.length; i++){
            newArr[i] = arr[i];
        }
    }
}
```

练习5：6名评委打分，分数范围是0~100的整数，由键盘录入。选手的最终得分是去掉最高分和最低分然后求平均，输出最终的得分。
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int[] score = new int[6];
        int sum = 0;
        for(int i = 0; i < score.length; i++){
            System.out.println("请输入第" + (i + 1) + "个评委的打分：");
            score[i] = sc.nextInt();
            sum += score[i];
        }
        int min = score[0];
        int max = score[0];
        for(int i = 0; i < score.length; i++){
            min = min < score[i] ? min : score[i];
            max = max > score[i] ? max : score[i];
        }
        double finalScore = (sum - min - max) / (score.length - 2.0);
        System.out.println("最终的得分为：" + finalScore);
    }
}
```

练习6：数字加密。某系统的数字密码(大于0)，采用加密方式进行传输。规则：先得到每位数，然后每位数都加上5，然后取末位，最后将所有数字反转，得到密文。设计程序，键盘录入数字密码的明文，得到密文并输出。
```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入明文：");
        int plainText = sc.nextInt();
        int cipherText = 0;
        while(plainText > 0){
            int lastDigit = plainText % 10;
            plainText /= 10;
            int temp = (lastDigit + 5) % 10;
            cipherText = cipherText * 10 + temp;
        }
        System.out.println("密文为：" + cipherText);
    }
}
```

练习7：数字解密。在练习6的条件下，设计程序，键盘录入数字密码的密文，得到明文并输出。

```
分析：
解密的第一步是将所有数字反转，这很容易办到

解密的第二步是%10的逆运算，显然很难办，但是仔细想想，由于最开始加密的时候，取的每个位置必定是0~9，加5之后必定是5~14，因此%10之后刚好这些数字没有多重对应关系，也就是5~9的数字对于%10的逆运算得到的必定是本身，0~4的数字对应%10的逆运算得到的必定是一一对应的10~14，那么第二步也可以很容易的得到了

解密的第三步减5，然后拼在一起，这很容易办到
```

```java
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入密文：");
        int cipherText = sc.nextInt();
        int plainText = 0;
        int temp;
        while(cipherText > 0){
            int lastDigit = cipherText % 10;
            cipherText /= 10;
            if(lastDigit >= 0 && lastDigit <= 4){
                temp = (lastDigit + 10) - 5;
            }else{
                temp = lastDigit - 5;
            }
            plainText = plainText * 10 + temp;
        }
        System.out.println("明文为：" + plainText);
    }
}
```

**当然，练习7用练习6的相同代码也可以解出来(doge)**

练习8：抽奖。奖金{2，588，888，1000，10000}，使用代码模拟抽奖，打印出每个奖项，奖项的出现顺序要随机且不重复。

```
分析：
由于要不重复，因此用随机数取数组元素的方法不可行。
可以通过先打乱数组，然后遍历输出数组的方式达到该效果。
```

```java
import java.util.Random;

public class Test{
    public static void main(String[] args){
        int[] money = {2,588,888,1000,10000};
        Random r = new Random();
        for(int i = 0; i < money.length; i++){
            int index = r.nextInt(money.length);
            int temp = money[i];
            money[i] = money[index];
            money[index] = temp;
        }
        for(int i = 0; i < money.length; i++){
            System.out.println("价值" + money[i] + "元的奖金被抽出");
        }
    }
}
```

练习9：模拟双色球彩票系统。投注号码由6个红色球号码和1个蓝色球号码组成。红色球号码从1-33中选择，蓝色球号码从1-16中选择。按（红球中的个数+蓝球中的个数）来划分中奖高低。0+1，1+1，2+1均为六等奖（奖金5元）；3+1，4+0均为五等奖（奖金10元）；4+1，5+0均为四等奖（奖金200元）；5+1为三等奖（奖金3000元）；6+0为二等奖（奖金最高500万）；6+1为一等奖（奖金最高1000万）。键盘依次录入你选择的号码，输出你获奖的奖项和奖金。
```java
import java.util.Random;
import java.util.Scanner;

public class Test{
    public static void main(String[] args){
        int[] winningNumbers = new int[7];
        int[] choiceNumbers = new int[7];
        int[] randomNumbers = new int[33];
        for(int i = 0; i < randomNumbers.length; i++){
            randomNumbers[i] = i + 1;
        }
        Random r = new Random();
        int temp;
        for(int i = 0; i < randomNumbers.length; i++){
            int index = r.nextInt(randomNumbers.length);
            temp = randomNumbers[i];
            randomNumbers[i] = randomNumbers[index];
            randomNumbers[index] = temp;
        }
        for(int i = 0; i < winningNumbers.length - 1; i++){
            winningNumbers[i] = randomNumbers[i];
        }
        winningNumbers[winningNumbers.length - 1] = r.nextInt(1,17); 
        Scanner sc = new Scanner(System.in);
        boolean flag = true;
        int count;
        for(int i = 0; i < choiceNumbers.length - 1; ){
            count = 0;
            if(flag){
                System.out.println("请输入您要选择的红球的第" + (i + 1) + "个号码：");
            }
            temp = sc.nextInt();
            for(int j = 0; j < i; j++){
                if(choiceNumbers[j] == temp){
                    count++;
                }
            }
            if(temp >= 1 && temp <= 33 && count == 0){
                choiceNumbers[i] = temp;
                i++;
                flag = true;
            }else if(temp < 1 || temp > 33){
                System.out.println("您输入的红球号码超过支持的范围(1~33)，请重新输入您的第" + (i + 1) + "个号码：");
                flag = false;
            }else if(count > 0){
                System.out.println("您输入的红球号码已存在，请重新输入您的第" + (i + 1) + "个号码：");
                flag = false;
            }
        }
        System.out.println("请输入您要选择的蓝球的号码：");
        while(flag){
            temp = sc.nextInt();
            if(temp >= 1 && temp <= 16){
                choiceNumbers[choiceNumbers.length - 1] = temp;
                flag = false;
            }else{
                System.out.println("您输入的蓝球号码超过支持的范围(1~16)，请重新输入您的蓝球号码：");
            }
        }
        int rightRed = 0;
        int rightBlue = 0;
        for(int i = 0; i < choiceNumbers.length - 1; i++){
            for(int j = 0; i + j < winningNumbers.length - 1; j++){
                if(choiceNumbers[i] == winningNumbers[i + j]){
                    rightRed++;
                }
            }
        }
        if(choiceNumbers[choiceNumbers.length - 1] == winningNumbers[winningNumbers.length - 1]){
            rightBlue++;
        }
        if(rightRed == 6 && rightBlue == 1){
            System.out.println("恭喜你获得一等奖，奖金最高1000万！");
        }else if(rightRed == 6 && rightBlue == 0){
            System.out.println("恭喜你获得二等奖，奖金最高500万！");
        }else if(rightRed == 5 && rightBlue == 1){
            System.out.println("恭喜你获得三等奖，奖金3000元！");
        }else if((rightRed == 5 && rightBlue == 0)||(rightRed == 4 && rightBlue == 1)){
            System.out.println("恭喜你获得四等奖，奖金200元！");
        }else if((rightRed == 4 && rightBlue == 0)||(rightRed == 3 && rightBlue == 1)){
            System.out.println("恭喜你获得五等奖，奖金10元！");
        }else if((rightRed == 2 && rightBlue == 1)||(rightRed == 1 && rightBlue == 1)||(rightRed == 0 && rightBlue == 1)){
            System.out.println("恭喜你获得六等奖，奖金5元！");
        }else{
            System.out.println("好可惜，没有中奖，下次继续努力-_-");
        }
    }
}
```

