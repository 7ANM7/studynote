# Java笔记

![image-20241107095246422](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241107095246422.png)

输出语句

```java
System.out.println("");
```

## 1.基本数据类型

![image-20241107012318487](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241107012318487.png)



格式：数据类型 变量名=数据值

例如:`int number=123;`  `double decimal=0.123;` 

`long l=99999999L;`(**long类型的变量在数据值后面加个L作为后缀**)

`float f=0.1234f;`(**float类型的变量在数据值后面加入F/f作为后缀**)

`boolean o=true;` 	`char c='好'；`	

`String name="安卓组"；`（**注意S是大写**）

## 2. 标识符

![image-20241107100419262](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241107100419262.png)

## 3. 输入

![image-20241107101058381](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241107101058381.png)



## 4.运算符

### +-*/%都和c语言一样

![image-20241107225807186](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241107225807186.png)

### **自动类型转换和强制类型转换**

+ 自动类型转换

1. 把一个==取值范围小==的数值，转成==取值范围大==的数据

byte<short<int<long<float<double 

```java
int a=10;
double b=a;
System.out.println(b);//输出为10.0
```

执行到double语句时，整数类型的a就自动变成double小数类型，即b=10.0

![image-20241108003119341](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108003119341.png)

2. byte short char 三种类型的数据在运算的时候，都会直接先提升为int，然后在进行运算

```java
byte b = 10;
short s = 20;
int result1 = b + s; // 结果是30
System.out.println(result1); // 输出: 30
```

b和s分别被提升为int类型（即10和20），然后执行加法运算得到结果30。

+ 强制类型转换

  1. 如果把一个==取值范围大==的数值，赋值给==取值范围小==的变量。是不允许直接赋值的。如果一定要这么做就需要加入强制转换

  2. ==格式==：目标数据类型 变量名=**（目标数据类型）**被强转的数据

  ```java
  double a=12.3;
  int b=(int)a;
  System.out,println(b);//输出：12  小数部分丢失
  ```

  ![image-20241108005048772](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108005048772.png)

  有时候会直接报错

### 字符串的“+”操作

+ 当“+”操作中出现字符串时，这个“+”是字符串连接符，而不是算术运算符了。会将前后的数据进行拼接，并产生一个新的字符串。

  例：“123”+123 -> “123123”

+  连续进行“+”操作时，==从左到右==逐个执行。

  例：1+99+“岁生日” -> “100岁生日”

  ​			1+2+“abc”+2+1-c> “3abc12”

### 字符的+操作

+ 当（字符+字符）/（字符+数字）时。会把字符通过ASCII码表查询对应的数字再计算。

  例：`System.out.println(1+'a');  //98`。

### 自增自减运算符（和c语言一样）

+ 经典

![image-20241108112053921](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108112053921.png)

### 赋值运算符（同c）

![image-20241108112154713](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108112154713.png)

### 关系运算符

![image-20241108112848328](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108112848328.png)

关系运算符的==结果==都是==boolean==类型，要么是true，要么是false。

```java
int a=10;
int b=20;
int c=10;
System.out.println(a==b);//false
System.out.println(a==c);//true
```

### 逻辑运算符

![image-20241108113648950](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108113648950.png)

```java
System.out.println(true & true);//true
System.out.println(false & false);//false
System.out.println(true & false);//false
System.out.println(true | false);//true
System.out.println(false | false);//false
System.out.println(true ^ false);//true
System.out.println(true ^ true);//false
System.out.println(!true);//false
System.out.println(!false);//true
```

+ 短路逻辑运算符

  ![image-20241108115059471](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108115059471.png)

  短路效果：当第一个条件不符合时，就不去判断第二个，提高效率

  即：&&:左边为false,右边不管是真是假,整个表达式的结果一定是false。
  		||:左边为true,右边不管是真是假,整个表达式的结果一定是true。

**最常用的逻辑运算符：&&，||，！**

### 三元运算符

格式：`关系表达式？表达式1：表达式2;`

计算规则:

1. 首先计算关系表达式的值

2. 如果值为true,表达式1的值就是运算结果

3. 如果值为false,表达式2的值就是运算结果

例：

```java
int a=10;
int b=20;
System.out.println(a>b?a:b)//20
```

### 运算符优先级

![image-20241108121145061](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108121145061.png)

## 5.方法（类似c的函数）

方法是程序当中最小的执行单元

### 最简单的定义和调用

```java
public staic void 方法名（参数）
{
    方法体;
}
```

​		调用格式：`方法名();`

### 带参数的方法的定义和调用

```java
public static void 方法名(参数1,参数2,.....)
{
    方法体;
}
```

​		调用：`方法名(参数1，参数2......)`

+ **方法调用时,参数的数量与类型必须与方法定义中小括号里面的变量一一对应,否则程序将报错。**

+ 形参：形式参数，是指方法==定义==中的参数

  实参：实际参数，方法==调用==的参数

  ![image-20241108142427536](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108142427536.png)

### 带返回值的方法定义和调用

```java
public static 返回值类型 方法名（参数）
{
    方法体；
    return 返回值；
}
```

直接调用：`方法名(实参);`

赋值调用：`整数类型 变量名=方法名（实参）；`

输出调用：`System.out.println(方法名(实参));`

例子：输入2组长和宽，求出对应的长方形面积，并比较大小

![image-20241108145120122](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20241108145120122.png)