# day1

## 注释

1.java规范的三种注释方式：

> 单行注释
>
> 多行注释
>
> 文档注释(java特有)

\2. 单行注释和多行注释的作用： ① 对所写的程序进行解释说明，增强可读性。方便自己，方便别人 ② 调试所写的代码

3.特点：单行注释和多行注释，注释了的内容不参与编译。换句话说，编译以后生成的.class结尾的字节码文件中不包含注释掉的信息

4.文档注释的使用：注释内容可以被JDK提供的工具 javadoc 所解析，生成一套以网页文件形式体现的该程序的说明文档。

5.多行注释不可以嵌套使用

## 对第一个java程序进行总结

1.java程序编写-编译-运行的过程 编写：我们将编写的java代码保存在以".java"结尾的源文件中 编译：使用javac.exe命令编译我们的java源文件。格式：javac 源文件名.java 运行：使用java.exe命令解释运行我们的字节码文件。 格式：java 类名

2.在一个java源文件中可以声明多个class。但是，只能最多有一个类声明为public的。 而且要求声明为public的类的类名必须与源文件名相同。

3.程序的入口是main()方法。格式是固定的。

4.输出语句： System.out.println():先输出数据，然后换行 System.out.print():只输出数据

5.每一行执行语句都以";"结束。

6.编译的过程：编译以后，会生成一个或多个字节码文件。字节码文件的文件名与java源文件中的类名相同。

# day2

## 计算机中不同进制的使用说明

对于整数，有四种表示方式：

> 二进制(binary)：0,1 ，满2进1.以0b或0B开头。
>
> 十进制(decimal)：0-9 ，满10进1。
>
> 八进制(octal)：0-7 ，满8进1. 以数字0开头表示。
>
> 十六进制(hex)：0-9及A-F，满16进1. 以0x或0X开头表示。此处的A-F不区分大小写。如：0x21AF +1= 0X21B0

## 标识符的使用

1.标识符：凡是自己可以起名字的地方都叫标识符。

> 比如：类名、变量名、方法名、接口名、包名...

2.标识符的命名规则：--> 如果不遵守如下的规则，编译不通过！需要大家严格遵守

> 由26个英文字母大小写，0-9 ，_或 $ 组成
>
> 数字不可以开头。
>
> 不可以使用关键字和保留字，但能包含关键字和保留字。
>
> Java中严格区分大小写，长度无限制。
>
> 标识符不能包含空格。

3.Java中的名称命名规范： --->如果不遵守如下的规范，编译可以通过！建议大家遵守

> 包名：多单词组成时所有字母都小写：xxxyyyzzz
>
> 类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz
>
> 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
>
> 常量名：所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ

\4. 注意1：在起名字时，为了提高阅读性，要尽量有意义，“见名知意”。

注意2：java采用unicode字符集，因此标识符也可以使用汉字声明，但是不建议使用。

## String类型变量的使用

1.String属于引用数据类型,翻译为：字符串

2.声明String类型变量时，使用一对""

3.String可以和8种基本数据类型变量做运算，且运算只能是连接运算：+

4.运算的结果仍然是String类型

## 变量的使用

1.java定义变量的格式：数据类型 变量名 = 变量值;

2.说明： ① 变量必须先声明，后使用 ② 变量都定义在其作用域内。在作用域内，它是有效的。换句话说，出了作用域，就失效了 ③ 同一个作用域内，不可以声明两个同名的变量

## Java定义的数据类型

一、变量按照数据类型来分：



```
基本数据类型：
    整型：byte \ short \ int \ long
    浮点型：float \ double
    字符型：char
    布尔型：boolean
引用数据类型：
类(class)
接口(interface)
数组(array)
```



1.**整型**：byte(1字节=8bit) \ short(2字节) \ int(4字节) \ long(8字节)

① byte范围：-128 ~ 127

② 声明long型变量，必须以"l"或"L"结尾

③ 通常，定义整型变量时，使用int型。

2.**浮点型**：float(4字节) \ double(8字节)

① 浮点型，表示带小数点的数值

② float表示数值的范围比long还大

③ 定义float类型变量时，变量要以"f"或"F"结尾

④ 通常，定义浮点型变量时，使用double型。

3.**字符型**：char (1字符=2字节)

① 定义char型变量，通常使用一对'',内部只能写一个字符

② 表示方式：1.声明一个字符 2.转义字符 3.直接使用 Unicode 值来表示字符型常量



```
char c5 = '\n';//换行符
char c6 = '\u0043';//Unicode
```



4.**布尔型**：boolean

① 只能取两个值之一：true 、 false

② 常常在条件判断、循环结构中使用

二、变量在类中声明的位置：成员变量 vs 局部变量

## 自动类型提升：

结论：当容量小的数据类型的变量与容量大的数据类型的变量做运算时，结果自动提升为容量大的数据类型。 byte 、char 、short --> int --> long --> float --> double

特别的：当byte、char、short三种类型的变量做运算时，结果为int型

说明：此时的容量大小指的是，表示数的范围的大和小。比如：float容量要大于long的容量

## 强制类型转换：

自动类型提升运算的逆运算。

1.需要使用强转符：()

2.注意点：强制类型转换，可能导致精度损失。

```
double d1 = 12.9;
//精度损失举例1
int i1 = (int)d1;//强制类型转换，截断操作
System.out.println(i1);//12
//精度损失举例2
int i2 = 128;
byte b = (byte)i2;
System.out.println(b);//-128
```

# day3

## 运算符之一：算术运算符

加+、 减-、 乘*、 除/、 取余%

自增自减：

(前)++ (后)++ (前)-- (后)--



```
(前)++ :先自增1，后运算
(后)++ :先运算，后自增1
自减同理
```

## 运算符之二：赋值运算符

=、 +=、 -=、 *=、 /=、 %=



```
开发中，如果希望变量实现+2的操作，有几种方法？(前提：int num = 10;)
方式一：num = num + 2;
方式二：num += 2; (推荐)
如果希望变量实现+1的操作：num++; (推荐)
```



## 运算符之三：比较运算符

==、 !=、 >、 <、 >=、 <=、 instanceof

结论： 1.比较运算符的结果是boolean类型 2.区分 == 和 =

特别说明：instanceof是Java中的二元运算符，左边是对象，右边是类；当对象是右边类或子类所创建对象时，返回true；否则，返回false。

## 运算符之四：逻辑运算符

&、 &&、 |、 ||、 !、 ^、

说明： 1.逻辑运算符操作的都是boolean类型的变量

区分& 与 &&：

相同点1：& 与 && 的运算结果相同

相同点2：当符号左边是true时，二者都会执行符号右边的运算

不同点：当符号左边是false时，&继续执行符号右边的运算。&&不再执行符号右边的运算。

*开发中，推荐使用&&*

区分：| 与 || ：

相同点1：| 与 || 的运算结果相同

相同点2：当符号左边是false时，二者都会执行符号右边的运算

不同点3：当符号左边是true时，|继续执行符号右边的运算，而||不再执行符号右边的运算

*开发中，推荐使用||*

## 运算符之五：位运算符 （了解）

结论： 1. 位运算符操作的都是整型的数据 2. "<<"符号表示在一定范围内，每向左移1位，相当于 * 2；">>"符号表示在一定范围内，每向右移1位，相当于 / 2

## 运算符之六：三元运算符

1.结构：(条件表达式)? 表达式1 : 表达式2



```
//获取两个整数的较大值
int m = 12;
int n = 5;
int max = (m > n)? m : n;
System.out.println(max);
```



2.说明： ① 条件表达式的结果为boolean类型 ② 根据条件表达式真或假，决定执行表达式1，还是表达式2. 如果表达式为true，则执行表达式1。 如果表达式为false，则执行表达式2。 ③ 表达式1 和表达式2要求是一致的。 ④ 三元运算符可以嵌套使用

3.凡是可以使用三元运算符的地方，都可以改写为if-else，反之，不成立。

4.如果程序既可以使用三元运算符，又可以使用if-else结构，那么优先选择三元运算符。原因：简洁、执行效率高。

# day4

## 分支结构中的if-else（条件判断结构）

一、三种结构

第一种：



```
if(条件表达式){
    执行表达式
}
```

第二种：二选一



```
if(条件表达式){
    执行表达式1
}else{
    执行表达式2
}
```

第三种：n选一



```
if(条件表达式){
    执行表达式1
}else if(条件表达式){
    执行表达式2
}else if(条件表达式){
    执行表达式3
}
...
else{
    执行表达式n
}
```

说明：

1.if-else结构是可以相互嵌套的。

2.如果if-else结构中的执行语句只有一行时，对应的一对{}可以省略的。但是，不建议大家省略。

## 如何从键盘获取不同类型的变量：需要使用Scanner类

具体实现步骤：

1.导包：import java.util.Scanner;

2.Scanner的实例化:Scanner scan = new Scanner(System.in);

3.调用Scanner类的相关方法（next() / nextXxx()），来获取指定类型的变量

注意： 需要根据相应的方法，来输入指定类型的值。如果输入的数据类型与要求的类型不匹配时，会报异常：InputMisMatchException导致程序终止。

举个例子









```java
//1.导包：import java.util.Scanner;
import java.util.Scanner;
class ScannerTest{
public static void main(String[] args){
    //2.Scanner的实例化
    Scanner scan = new Scanner(System.in);

    //3.调用Scanner类的相关方法
    System.out.println(&quot;请输入你的姓名：&quot;);
    String name = scan.next();
    System.out.println(name);

    System.out.println(&quot;请输入你的芳龄：&quot;);
    int age = scan.nextInt();
    System.out.println(age);

    System.out.println(&quot;请输入你的体重：&quot;);
    double weight = scan.nextDouble();
    System.out.println(weight);

    System.out.println(&quot;你是否相中我了呢？(true/false)&quot;);
    boolean isLove = scan.nextBoolean();
    System.out.println(isLove);

    //对于char型的获取，Scanner没有提供相关的方法。只能获取一个字符串
    System.out.println(&quot;请输入你的性别：(男/女)&quot;);
    String gender = scan.next();//&quot;男&quot;
    char genderChar = gender.charAt(0);//获取索引为0位置上的字符
    System.out.println(genderChar);
	}
}
```



## 分支结构之二：switch-case

1.格式



```
switch(表达式){
case 常量1:
    执行语句1;
    //break;
case 常量2:
执行语句2;
//break;
...
default:
执行语句n;
//break;
}
```



2.说明：

① 根据switch表达式中的值，依次匹配各个case中的常量。一旦匹配成功，则进入相应case结构中，调用其执行语句。 当调用完执行语句以后，则仍然继续向下执行其他case结构中的执行语句，直到遇到break关键字或此switch-case结构 末尾结束为止。

② break,可以使用在switch-case结构中，表示一旦执行到此关键字，就跳出switch-case结构

③ switch结构中的表达式，只能是如下的6种数据类型之一： byte 、short、char、int、枚举类型(JDK5.0新增)、String类型(JDK7.0新增)

④ case 之后只能声明常量。不能声明范围。

⑤ break关键字是可选的。

⑥ default:相当于if-else结构中的else.
default结构是可选的，而且位置是灵活的。

⑦ 如果switch-case结构中的多个case的执行语句相同，则可以考虑进行合并。

## For循环结构的使用

一、循环结构的4个要素 ① 初始化条件 ② 循环条件 --->是boolean类型 ③ 循环体 ④ 迭代条件

二、for循环的结构

for(①;②;④){ ③ }

执行过程：① - ② - ③ - ④ - ② - ③ - ④ - ... - ②

# day5

## 嵌套循环的使用

1.嵌套循环：将一个循环结构A声明在另一个循环结构B的循环体中,就构成了嵌套循环

\2. 外层循环：循环结构B 内层循环：循环结构A

3.说明 ① 内层循环结构遍历一遍，只相当于外层循环循环体执行了一次 ② 假设外层循环需要执行m次，内层循环需要执行n次。此时内层循环的循环体一共执行了m * n次

4.技巧：外层循环控制行数，内层循环控制列数

## While 循环的使用

一、循环结构的4个要素 ① 初始化条件 ② 循环条件 --->是boolean类型 ③ 循环体 ④ 迭代条件

二、while循环的结构



```
①
while(②){
    ③;
    ④;
}
```

执行过程：① - ② - ③ - ④ - ② - ③ - ④ - ... - ②

说明： 1.写while循环千万小心不要丢了迭代条件。一旦丢了，就可能导致死循环！ 2.我们写程序，要避免出现死循环。 3.for循环和while循环是可以相互转换的！ 区别：for循环和while循环的初始化条件部分的作用范围不同。

算法：有限性。

## do-while循环的使用

一、循环结构的4个要素 ① 初始化条件 ② 循环条件 --->是boolean类型 ③ 循环体 ④ 迭代条件

二、do-while循环结构：



```
①
do{
    ③;
    ④;
}while(②);
```



执行过程：① - ③ - ④ - ② - ③ - ④ - ... - ②

说明： 1.do-while循环至少会执行一次循环体！ 2.开发中，使用for和while更多一些。较少使用do-while

## break和continue关键字的使用

| 关键字   | 使用范围              | 循环中使用的作用(不同点) |           相同点           |
| :------- | :-------------------- | :----------------------- | :------------------------: |
| break    | switch-case循环结构中 | 结束当前循环             | 关键字后面不能声明执行语句 |
| continue | 循环结构中            | 结束当次循环             | 关键字后面不能声明执行语句 |





# day6

## 一、数组的概述

1.数组的理解：数组(Array)，是多个相同类型数据按一定顺序排列的集合，并使用一个名字命名，并通过编号的方式对这些数据进行统一管理。

2.数组相关的概念：

> 数组名
>
> 元素
>
> 角标、下标、索引
>
> 数组的长度：元素的个数

3.数组的特点：

1）数组是有序排列的

2）数组属于引用数据类型的变量。数组的元素，既可以是基本数据类型，也可以是引用数据类型

3）创建数组对象会在内存中开辟一整块连续的空间 4）数组的长度一旦确定，就不能修改。

4.数组的分类： ① 按照维数：一维数组、二维数组、。。。 ② 按照数组元素的类型：基本数据类型元素的数组、引用数据类型元素的数组

5.一维数组的使用 ① 一维数组的声明和初始化

② 如何调用数组的指定位置的元素

③ 如何获取数组的长度

④ 如何遍历数组

*ArrayTest.java*





publicclassArrayTest {



```
public static void main(String[] args) {

    //1. 一维数组的声明和初始化
    int num;//声明
    num = 10;//初始化
    int id = 1001;//声明 + 初始化

    int[] ids;//声明
    //1.1 静态初始化:数组的初始化和数组元素的赋值操作同时进行
    ids = new int[]{1001,1002,1003,1004};
    //1.2动态初始化:数组的初始化和数组元素的赋值操作分开进行
    String[] names = new String[5];

    //错误的写法：
```



//      int[] arr1 = new int[];
 //      int[5] arr2 = new int[5];
 //      int[] arr3 = new int[3]{1,2,3};



```
    //也是正确的写法：
    int[] arr4 = {1,2,3,4,5};//类型推断

    //总结：数组一旦初始化完成，其长度就确定了。

    //2.如何调用数组的指定位置的元素:通过角标的方式调用。
    //数组的角标（或索引）从0开始的，到数组的长度-1结束。
    names[0] = &quot;王铭&quot;;
    names[1] = &quot;王赫&quot;;
    names[2] = &quot;张学良&quot;;
    names[3] = &quot;孙居龙&quot;;
    names[4] = &quot;王宏志&quot;;//charAt(0)
```



//      names[5] = "周扬";



```
    //3.如何获取数组的长度。
    //属性:length
    System.out.println(names.length);//5
    System.out.println(ids.length);

    //4.如何遍历数组
    /*System.out.println(names[0]);
    System.out.println(names[1]);
    System.out.println(names[2]);
    System.out.println(names[3]);
    System.out.println(names[4]);*/

    for(int i = 0;i &lt; names.length;i++){
        System.out.println(names[i]);
    }
}
```



}



------

⑤ 数组元素的默认初始化值

> 数组元素是整型：0
>
> 数组元素是浮点型：0.0
>
> 数组元素是char型：0或'\u0000'，而非'0'
>
> 数组元素是boolean型：false
>
> 数组元素是引用数据类型：null

⑥ 数组的内存解析





publicclassArrayTest1 {



```
public static void main(String[] args) {
    //5.数组元素的默认初始化值
    int[] arr = new int[4];
    for(int i = 0;i &lt; arr.length;i++){
        System.out.println(arr[i]);
    }
    System.out.println(&quot;**********&quot;);

    short[] arr1 = new short[4];
    for(int i = 0;i &lt; arr1.length;i++){
        System.out.println(arr1[i]);
    }
    System.out.println(&quot;**********&quot;);
    float[] arr2 = new float[5];
    for(int i = 0;i &lt; arr2.length;i++){
        System.out.println(arr2[i]);
    }

    System.out.println(&quot;**********&quot;);
    char[] arr3 = new char[4];
    for(int i = 0;i &lt; arr3.length;i++){
        System.out.println(&quot;----&quot; + arr3[i] + &quot;****&quot;);
    }

    if(arr3[0] == 0){
        System.out.println(&quot;你好！&quot;);
    }

    System.out.println(&quot;**********&quot;);
    boolean[] arr4 = new boolean[5];
    System.out.println(arr4[0]);

    System.out.println(&quot;**********&quot;);
    String[] arr5 = new String[5];
    System.out.println(arr5[0]);
    if(arr5[0] == null){
        System.out.println(&quot;北京天气不错！&quot;);
    }
}
```



}



------

## 二维数组的使用

1.理解：对于二维数组的理解，我们可以看成是一维数组array1又作为另一个一维数组array2的元素而存在。其实，从数组底层的运行机制来看，其实没有多维数组。

2.二维数组的使用:

① 二维数组的声明和初始化

② 如何调用数组的指定位置的元素

③ 如何获取数组的长度

④ 如何遍历数组





publicclassArrayTest2 {



publicstaticvoidmain(String[] args) {



//1.二维数组的声明和初始化



int[] arr=newint[]{1,2,3};//一维数组



//静态初始化



int[][] arr1=newint[][]{{1,2,3},{4,5},{6,7,8}};



//动态初始化1



String[][] arr2=newString[3][2];



//动态初始化2



String[][] arr3=newString[3][];



//错误的情况



//String[][] arr4=newString[][4];



//String[4][3] arr5=newString[][];



//int[][] arr6=newint[4][3]{{1,2,3},{4,5},{6,7,8}};



```
    //也是正确的写法：
    int[] arr4[] = new int[][]{{1,2,3},{4,5,9,10},{6,7,8}};
    int[] arr5[] = {{1,2,3},{4,5},{6,7,8}};

    //2.如何调用数组的指定位置的元素
    System.out.println(arr1[0][1]);//2
    System.out.println(arr2[1][1]);//null

    arr3[1] = new String[4];
    System.out.println(arr3[1][0]);

    //3.获取数组的长度
    System.out.println(arr4.length);//3
    System.out.println(arr4[0].length);//3
    System.out.println(arr4[1].length);//4

    //4.如何遍历二维数组
    for(int i = 0;i &lt; arr4.length;i++){

        for(int j = 0;j &lt; arr4[i].length;j++){
            System.out.print(arr4[i][j] + &quot;  &quot;);
        }
        System.out.println();
    }

}
```



}



------

规定：二维数组分为外层数组的元素，内层数组的元素



```
int[][] arr = new int[4][3];
```

> 外层元素：arr[0],arr[1]等
>
> 内层元素：arr[0][0],arr[1][2]等

⑤ 数组元素的默认初始化值

针对于初始化方式一：比如：`int[][] arr = new int[4][3];`

> 外层元素的初始化值为：地址值
>
> 内层元素的初始化值为：与一维数组初始化情况相同

针对于初始化方式二：比如：`int[][] arr = new int[4][];`

> 外层元素的初始化值为：null
>
> 内层元素的初始化值为：不能调用，否则报错。

⑥ 数组的内存解析





publicclassArrayTest3 {



public static void main(String[] args) {



```
    int[][] arr = new int[4][3];
    System.out.println(arr[0]);//[I@15db9742 
    System.out.println(arr[0][0]);//0
```



//      System.out.println(arr);//[[I@6d06d69c



```
    System.out.println(&quot;*****************&quot;);
    float[][] arr1 = new float[4][3];
    System.out.println(arr1[0]);//地址值
    System.out.println(arr1[0][0]);//0.0

    System.out.println(&quot;*****************&quot;);

    String[][] arr2 = new String[4][2];
    System.out.println(arr2[1]);//地址值
    System.out.println(arr2[1][1]);//null

    System.out.println(&quot;*****************&quot;);
    double[][] arr3 = new double[4][];
    System.out.println(arr3[1]);//null
```



//      System.out.println(arr3[1][0]);//报错



```
}
```



}



------

# day7

## java.util.Arrays

操作数组的工具类，里面定义了很多操作数组的方法

1.boolean equals(int[] a,int[] b):判断两个数组是否相等。

2.String toString(int[] a):输出数组信息。

3.void fill(int[] a,int val):将指定值填充到数组之中。

4.void sort(int[] a):对数组进行排序。

5.int binarySearch(int[] a,int key)

例子：





import java.util.Arrays;



public class ArraysTest {
 public static void main(String[] args) {



```
    //1.boolean equals(int[] a,int[] b):判断两个数组是否相等。
    int[] arr1 = new int[]{1,2,3,4};
    int[] arr2 = new int[]{1,3,2,4};
    boolean isEquals = Arrays.equals(arr1, arr2);
    System.out.println(isEquals);

    //2.String toString(int[] a):输出数组信息。
    System.out.println(Arrays.toString(arr1));


    //3.void fill(int[] a,int val):将指定值填充到数组之中。
    Arrays.fill(arr1,10);
    System.out.println(Arrays.toString(arr1));


    //4.void sort(int[] a):对数组进行排序。
    Arrays.sort(arr2);
    System.out.println(Arrays.toString(arr2));

    //5.int binarySearch(int[] a,int key)
    int[] arr3 = new int[]{-98,-34,2,34,54,66,79,105,210,333};
    int index = Arrays.binarySearch(arr3, 210);
    if(index &gt;= 0){
        System.out.println(index);
    }else{
        System.out.println(&quot;未找到&quot;);
    }


}
```



}



------

## 数组的复制、反转、查找(线性查找、二分法查找）





publicclass ArrayTest2 {



```
public static void main(String[] args) {

    String[] arr = new String[]{&quot;JJ&quot;,&quot;DD&quot;,&quot;MM&quot;,&quot;BB&quot;,&quot;GG&quot;,&quot;AA&quot;};


    //数组的复制(区别于数组变量的赋值：arr1 = arr)
    String[] arr1 = new String[arr.length];
    for(int i = 0;i &lt; arr1.length;i++){
        arr1[i] = arr[i];
    }

    //数组的反转
    //方法一：
```



//      for(int i = 0;i < arr.length / 2;i++){
 //          String temp = arr[i];
 //          arr[i] = arr[arr.length - i -1];
 //          arr[arr.length - i -1] = temp;
 //      }



```
    //方法二：
```



//      for(int i = 0,j = arr.length - 1;i < j;i++,j--){
 //          String temp = arr[i];
 //          arr[i] = arr[j];
 //          arr[j] = temp;
 //      }



```
    //遍历
    for(int i = 0;i &lt; arr.length;i++){
        System.out.print(arr[i] + &quot;\t&quot;);
    }

    System.out.println();
    //查找（或搜索）
    //线性查找：
    String dest = &quot;BB&quot;;
    dest = &quot;CC&quot;;

    boolean isFlag = true;

    for(int i = 0;i &lt; arr.length;i++){

        if(dest.equals(arr[i])){
            System.out.println(&quot;找到了指定的元素，位置为：&quot; + i);
            isFlag = false;
            break;
        }

    }
    if(isFlag){
        System.out.println(&quot;很遗憾，没有找到的啦！&quot;);

    }
    //二分法查找：(熟悉)
    //前提：所要查找的数组必须有序。
    int[] arr2 = new int[]{-98,-34,2,34,54,66,79,105,210,333};

    int dest1 = -34;
    dest1 = 35;
    int head = 0;//初始的首索引
    int end = arr2.length - 1;//初始的末索引
    boolean isFlag1 = true;
    while(head &lt;= end){

        int middle = (head + end)/2;

        if(dest1 == arr2[middle]){
            System.out.println(&quot;找到了指定的元素，位置为：&quot; + middle);
            isFlag1 = false;
            break;
        }else if(arr2[middle] &gt; dest1){
            end = middle - 1;
        }else{//arr2[middle] &lt; dest1
            head = middle + 1;
        }


    }

    if(isFlag1){
        System.out.println(&quot;很遗憾，没有找到的啦！&quot;);
    }


}
```



}



## 数组中的常见异常

1.数组角标越界的异常：ArrayIndexOutOfBoundsExcetion

2.空指针异常：NullPointerException

## 快速排序

通过一趟排序将待排序记录分割成独立的两部分，其中一部分记录的关键字均比另一部分关键字小，则分别对这两部分继续进行排序，直到整个序列有序。





publicclassQuickSort {



private static void swap(int[] data, int i, int j) {



int temp = data[i];



​        data[i] = data[j];



​        data[j] = temp;



​    }



```
private static void subSort(int[] data, int start, int end) {
    if (start &lt; end) {
        int base = data[start];
        int low = start;
        int high = end + 1;
        while (true) {
            while (low &lt; end &amp;&amp; data[++low] - base &lt;= 0)
                ;
            while (high &gt; start &amp;&amp; data[--high] - base &gt;= 0)
                ;
            if (low &lt; high) {
                swap(data, low, high);
            } else {
                break;
            }
        }
        swap(data, start, high);

        subSort(data, start, high - 1);//递归调用
        subSort(data, high + 1, end);
    }
}
public static void quickSort(int[] data){
    subSort(data,0,data.length-1);
}


public static void main(String[] args) {
    int[] data = { 9, -16, 30, 23, -30, -49, 25, 21, 30 };
    System.out.println(&quot;排序之前：\n&quot; + java.util.Arrays.toString(data));
    quickSort(data);
    System.out.println(&quot;排序之后：\n&quot; + java.util.Arrays.toString(data));
}
```



}



------

## 数组的冒泡排序的实现

```java
public class SE01 {
    public static void BubbleSort(int[] a) {
        for (int i = 0; i < a.length; i++) {
            for (int j = 0 ; j < a.length - 1-i; j++) {
                if(a[j+1]<a[j]){
                    int t = a[j];
                    a[j] = a[j + 1];
                    a[j + 1] = t;
                }
            }
        }
    }
    public static void main(String[] args) {
        int[] a = new int[]{3, 4, 2, 5, 7, 1, 8, 6, 9};
        System.out.println(Arrays.toString(a));
        BubbleSort(a);
        System.out.println(Arrays.toString(a));
    }
}
```



------

# day8

## 概述

一、Java面向对象学习的三条主线：（第4-6章） 1.Java类及类的成员：属性、方法、构造器；代码块、内部类

2.面向对象的三大特征：封装性、继承性、多态性、(抽象性)

3.其它关键字：this、super、stati

c、final、abstract、interface、package、import等

“大处着眼，小处着手”

二、“人把大象装进冰箱”

1.面向过程：强调的是功能行为，以函数为最小单位，考虑怎么做。

- ① 把冰箱门打开
- ② 抬起大象，塞进冰箱
- ③ 把冰箱门关闭

2.面向对象：强调具备了功能的对象，以类/对象为最小单位，考虑谁来做。

三、面向对象的两个要素：

类：对一类事物的描述，是抽象的、概念上的定义

对象：是实际存在的该类事物的每个个体，因而也称为实例(instance)

> 面向对象程序设计的重点是类的设计
>
> 设计类，就是设计类的成员。

## 类中方法的声明和使用

方法：描述类应该具有的功能。

比如：

> Math类：sqrt()\random() ...
>
> Scanner类：nextXxx() ...
>
> Arrays类：sort() \ binarySearch() \ toString() \ equals() \ ...

1.举例：



```
public void eat(){}`
public void sleep(int hour){}`
public String getName(){}
public String getNation(String nation){}
```

2.方法的声明：权限修饰符 返回值类型 方法名(形参列表){ 方法体 }

注意：static、final、abstract 来修饰的方法，后面再讲。

3.说明：

**3.1 关于权限修饰符**：默认方法的权限修饰符先都使用public

Java规定的4种权限修饰符：private、public、缺省、protected -->封装性再细说

**3.2 返回值类型**： 有返回值 vs 没有返回值

*3.2.1* 如果方法有返回值，则必须在方法声明时，指定返回值的类型。同时，方法中，需要使用return关键字来返回指定类型的变量或常量：“return 数据”。如果方法没有返回值，则方法声明时，使用void来表示。通常，没有返回值的方法中，就不需要使用return.但是，如果使用的话，只能“return;”表示结束此方法的意思。

*3.2.2* 我们定义方法该不该有返回值？

① 题目要求

② 凭经验：具体问题具体分析

**3.3 方法名**：属于标识符，遵循标识符的规则和规范，“见名知意”

**3.4 形参列表**： 方法可以声明0个，1个，或多个形参。

*3.4.1 格式*：数据类型1 形参1,数据类型2 形参2,...

*3.4.2* 我们定义方法时，该不该定义形参？

① 题目要求

② 凭经验：具体问题具体分析

**3.5 方法体**：方法功能的体现。

4.return关键字的使用：

**4.1使用范围**：使用在方法体中

**4.2.作用**：① 结束方法 ② 针对于有返回值类型的方法，使用"return 数据"方法返回所要的数据。

**4.3.注意点**：return关键字后面不可以声明执行语句。

5.方法的使用中，可以调用当前类的属性或方法

特殊的：方法A中又调用了方法A:递归方法。

方法中，不可以定义方法。

## 类中属性的使用

属性（成员变量） vs 局部变量

**1.相同点**：

1.1 *定义变量的格式*：数据类型 变量名 = 变量值

1.2 先声明，后使用

1.3 变量都有其对应的作用域

**2.不同点**：

2.1 在类中声明的位置的不同

属性：直接定义在类的一对{}内

局部变量：声明在方法内、方法形参、代码块内、构造器形参、构造器内部的变量

2.2 关于权限修饰符的不同

属性：可以在声明属性时，指明其权限，使用权限修饰符。

常用的权限修饰符：private、public、缺省、protected --->封装性

局部变量：不可以使用权限修饰符。

2.3 默认初始化值的情况：

属性：类的属性，根据其类型，都有默认初始化值。

> 整型（byte、short、int、long）：0
>
> 浮点型（float、double）：0.0
>
> 字符型（char）：0 （或'\u0000'）
>
> 布尔型（boolean）：false
>
> 引用数据类型（类、数组、接口）：null
>
> 局部变量：没有默认初始化值。

意味着，我们在调用局部变量之前，一定要显式赋值。

特别地：形参在调用时，我们赋值即可。

2.4 在内存中加载的位置：

属性：加载到堆空间中 （非static）

局部变量：加载到栈空间

## 类的其他说明

一、设计类，其实就是设计类的成员

属性 = 成员变量 = field = 域、字段

方法 = 成员方法 = 函数 = method

创建类的对象 = 类的实例化 = 实例化类

二、类和对象的使用（面向对象思想落地的实现）：

1.创建类，设计类的成员





//1.创建类，设计类的成员



classPerson{



```
//属性
String name;
int age = 1;
boolean isMale;

//方法
public void eat(){
    System.out.println(&quot;人可以吃饭&quot;);
}

public void sleep(){
    System.out.println(&quot;人可以睡觉&quot;);
}

public void talk(String language){
    System.out.println(&quot;人可以说话,使用的是：&quot; + language);
}
```



}



2.创建类的对象

3.通过“对象.属性”或“对象.方法”调用对象的结构

三、如果创建了一个类的多个对象，则每个对象都独立的拥有一套类的属性。（非static的）意味着：如果我们修改一个对象的属性a，则不影响另外一个对象属性a的值。

四、对象的内存解析

# day9

## 万事万物皆对象

一、理解“万事万物皆对象”

1.在Java语言范畴中，我们都将功能、结构等封装到类中，通过类的实例化，来调用具体的功能结构

> Scanner,String等
>
> 文件：File
>
> 网络资源：URL

2.涉及到Java语言与前端Html、后端的数据库交互时，前后端的结构在Java层面交互时，都体现为类、对象。

二、内存解析的说明

1.引用类型的变量，只可能存储两类值：null 或 地址值（含变量的类型）

三、匿名对象的使用

1.理解：我们创建的对象，没有显式的赋给一个变量名。即为匿名对象

2.特征：匿名对象只能调用一次。

3.使用：如下





publicclassInstanceTest {



public static void main(String[] args) {



​        Phone p = new Phone();



//      p = null;



​        System.out.println(p);



```
    p.sendEmail();
    p.playGame();


    //匿名对象
```



//      new Phone().sendEmail();
 //      new Phone().playGame();



```
    new Phone().price = 1999;
    new Phone().showPrice();//0.0

    //**********************************
    PhoneMall mall = new PhoneMall();
```



//      mall.show(p);
 //匿名对象的使用
 mall.show(new Phone());



```
}
```



}



class PhoneMall{



```
public void show(Phone phone){
    phone.sendEmail();
    phone.playGame();
}
```



}



class Phone{
 double price;//价格



```
public void sendEmail(){
    System.out.println(&quot;发送邮件&quot;);
}

public void playGame(){
    System.out.println(&quot;玩游戏&quot;);
}

public void showPrice(){
    System.out.println(&quot;手机价格为：&quot; + price);
}
```



}



## 方法的重载（overload）

1.定义：在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可。

"两同一不同":同一个类、相同方法名

参数列表不同：参数个数不同，参数类型不同

2.举例： Arrays类中重载的sort() / binarySearch()

3.判断是否是重载：跟方法的权限修饰符、返回值类型、形参变量名、方法体都没有关系！

4.在通过对象调用方法时，如何确定某一个指定的方法： 方法名 ---> 参数列表

## 可变个数形参的方法

1.jdk 5.0新增的内容

2.具体使用：

2.1 可变个数形参的格式：数据类型 ... 变量名



```jAVA
public void show(String ... strs)
```

2.2 当调用可变个数形参的方法时，传入的参数个数可以是：0个，1个,2个，。。。

2.3 可变个数形参的方法与本类中方法名相同，形参不同的方法之间构成重载

2.4 可变个数形参的方法与本类中方法名相同，形参类型也相同的数组之间不构成重载。换句话说，二者不能共存。

2.5 可变个数形参在方法的形参中，必须声明在末尾

2.6 可变个数形参在方法的形参中,最多只能声明一个可变形参。

## 关于变量的赋值：

如果变量是基本数据类型，此时赋值的是变量所保存的数据值。如果变量是引用数据类型，此时赋值的是变量所保存的数据的地址值。

## 方法的形参的传递机制：值传递

1.形参：方法定义时，声明的小括号内的参数

实参：方法调用时，实际传递给形参的数据

2.值传递机制：如果参数是基本数据类型，此时实参赋给形参的是实参真实存储的数据值。如果参数是引用数据类型，此时实参赋给形参的是实参存储数据的地址值。

# day10

## 面向对象的特征一：封装与隐藏 3W:what? why? how?

一、问题的引入：当我们创建一个类的对象以后，我们可以通过"对象.属性"的方式，对对象的属性进行赋值。这里，赋值操作要受到属性的数据类型和存储范围的制约。除此之外，没有其他制约条件。但是，在实际问题中，我们往往需要给属性赋值

加入额外的限制条件。这个条件就不能在属性声明时体现，我们只能通过方法进行限制条件的添加。（比如：`setLegs()`）同时，我们需要避免用户再使用"对象.属性"的方式对属性进行赋值。则需要将属性声明为私有的(private).

> 此时，针对于属性就体现了封装性。

二、封装性的体现： 我们将类的属性xxx私有化(private),同时，提供公共的(public)方法来获取(getXxx)和设置(setXxx)此属性的值

拓展：封装性的体现：① 如上 ② 不对外暴露的私有的方法 ③ 单例模式 ...





classAnimal{



```
String name;
private int age;
private int legs;//腿的个数

//对属性的设置
public void setLegs(int l){
    if(l &gt;= 0 &amp;&amp; l % 2 == 0){
        legs = l;
    }else{
        legs = 0;
        //抛出一个异常（暂时没有讲）
    }
}

//对属性的获取
public int getLegs(){
    return legs;
}
```



}



三、封装性的体现，需要权限修饰符来配合。

1.Java规定的4种权限（从小到大排列）：private、缺省、protected 、public

2.4种权限可以用来修饰类及类的内部结构：属性、方法、构造器、内部类

3.具体的，4种权限都可以用来修饰类的内部结构：属性、方法、构造器、内部类

> 修饰类的话，只能使用：缺省、public

- 总结封装性：Java提供了4种权限修饰符来修饰类及类的内部结构，体现类及类的内部结构在被调用时的可见性的大小。

## 四种访问权限修饰符

Java权限修饰符public、protected、private置于*类的成员*定义前，用来限定对象对该类成员的访问权限

| 修饰符    | 类内部 | 同一个包 | 不同包的子类 | 同一个工程 |
| :-------- | :----- | :------- | :----------- | :--------- |
| private   | Yes    |          |              |            |
| （缺省）  | Yes    | Yes      |              |            |
| protected | Yes    | Yes      | Yes          |            |
| public    | Yes    | Yes      | Yes          | Yes        |

对于class的权限修饰只可以用public和default（缺省）

> public类可以在任意地方被访问
>
> default类只可以被同一个包内部的类访问

## 构造器

一、构造器的作用：

1.创建对象

2.初始化对象的信息

二、说明：

1.如果没有显式的定义类的构造器的话，则系统默认提供一个空参的构造器

2.定义构造器的格式：权限修饰符 类名(形参列表){}

3.一个类中定义的多个构造器，彼此构成重载

4.一旦我们显式的定义了类的构造器之后，系统就不再提供默认的空参构造器

5.一个类中，至少会有一个构造器。

总结：属性赋值的先后顺序

① 默认初始化

② 显式初始化

③ 构造器中初始化

④ 通过"对象.方法" 或 "对象.属性"的方式，赋值

以上操作的先后顺序：① - ② - ③ - ④

## JaveBean

JavaBean是一种Java语言写成的可重用组件。

所谓JavaBean，是指符合如下标准的Java类：

> 类是公共的
>
> 有一个无参的公共的构造器
>
> 有属性，且有对应的get、set方法

## this关键字的使用

1.this可以用来修饰、调用：属性、方法、构造器

2.this修饰属性和方法：

this理解为：当前对象 或 当前正在创建的对象

2.1 在类的方法中，我们可以使用"this.属性"或"this.方法"的方式，调用当前对象属性或方法。但是，通常情况下，我们都选择省略"this."。特殊情况下，如果方法的形参和类的属性同名时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。

2.2 在类的构造器中，我们可以使用"this.属性"或"this.方法"的方式，调用当前正在创建的对象属性或方法。但是，通常情况下，我们都选择省略"this."。特殊情况下，如果构造器的形参和类的属性同名时，我们必须显式的使用"this.变量"的方式，表明此变量是属性，而非形参。

3.this调用构造器

① 我们在类的构造器中，可以显式的使用"this(形参列表)"方式，调用本类中指定的其他构造器

② 构造器中不能通过"this(形参列表)"方式调用自己

③ 如果一个类中有n个构造器，则最多有 n - 1构造器中使用了"this(形参列表)"

④ 规定："this(形参列表)"必须声明在当前构造器的首行

⑤ 构造器内部，最多只能声明一个"this(形参列表)"，用来调用其他的构造器

## package和import

一、package关键字的使用

1.为了更好的实现项目中类的管理，提供包的概念

2.使用package声明类或接口所属的包，声明在源文件的首行

3.包，属于标识符，遵循标识符的命名规则、规范(xxxyyyzzz)、“见名知意”

4.每"."一次，就代表一层文件目录。

补充：同一个包下，不能命名同名的接口、类。不同的包下，可以命名同名的接口、类。

二、import关键字的使用

import:导入

1.在源文件中显式的使用import结构导入指定包下的类、接口

2.声明在包的声明和类的声明之间

3.如果需要导入多个结构，则并列写出即可

4.可以使用"xxx.*"的方式，表示可以导入xxx包下的所有结构

5.如果使用的类或接口是java.lang包下定义的，则可以省略import结构

6.如果使用的类或接口是本包下定义的，则可以省略import结构

7.如果在源文件中，使用了不同包下的同名的类，则必须至少有一个类需要以全类名的方式显示。

8.使用"xxx.*"方式表明可以调用xxx包下的所有结构。但是如果使用的是xxx子包下的结构，则仍需要显式导入

9.import static:导入指定类或接口中的静态结构:属性或方法。

## MVC设计模式

MVC是常用的设计模式之一，将整个程序分为三个层次：视图模型层、控制器层与数据模型层。这种将程序输入输出、数据处理以及数据的展示分离开来的设计模式使程序结构变得灵活而且清晰，同时也描述了程序各个对象间的通信方式，降低了程序的耦合性。

模型层：model 主要处理数据

> 数据对象封装 model.bean/domain
>
> 数据库操作类 model.dao
>
> 数据库 model.db

控制层：controller 处理业务逻辑

> 应用界面相关 controller.activity
>
> 存放fragment controller.fragment
>
> 显示列表的适配器 controller.adapter
>
> 服务相关的 controller.service
>
> 抽取的基类controller.base

视图层：view 显示数据

> 相关工具类 view.utils 自定义 viwe.ui

## JDK中主要的包介绍

java.lang ------ 包含一些Java语言的核心类，如String、Math、Integer、System、Thread，提供常用功能

java.net ------ 包含执行与网络相关的操作的类和接口

java.io ------ 包含能够提供多种输入/输出功能的类

java.util ------ 包含一些实用工具类，如定义系统特性、接口的集合框架类、使用与日期日历相关的函数

java.text ------ 包含了一些java格式化相关的类

java.sql ------ 包含了java进行JDBC数据库编程的相关类/接口

java.awt ------ 包含了构成抽象窗口工具集（abstract window toolkits)的多个类，这些类被用来构建和管理应用程序的图形用户界面（GUI）



# day11

## Eclipse中的快捷键：



```
 * 1.补全代码的声明：alt + /
 * 2.快速修复: ctrl + 1  
 * 3.批量导包：ctrl + shift + o
 * 4.使用单行注释：ctrl + /
 * 5.使用多行注释： ctrl + shift + /   
 * 6.取消多行注释：ctrl + shift + \
 * 7.复制指定行的代码：ctrl + alt + down 或 ctrl + alt + up
 * 8.删除指定行的代码：ctrl + d
 * 9.上下移动代码：alt + up  或 alt + down
 * 10.切换到下一行代码空位：shift + enter
 * 11.切换到上一行代码空位：ctrl + shift + enter
 * 12.如何查看源码：ctrl + 选中指定的结构   或  ctrl + shift + t
 * 13.退回到前一个编辑的页面：alt + left 
 * 14.进入到下一个编辑的页面(针对于上面那条来说的)：alt + right
 * 15.光标选中指定的类，查看继承树结构：ctrl + t
 * 16.复制代码： ctrl + c
 * 17.撤销： ctrl + z
 * 18.反撤销： ctrl + y
 * 19.剪切：ctrl + x 
 * 20.粘贴：ctrl + v
 * 21.保存： ctrl + s
 * 22.全选：ctrl + a
 * 23.格式化代码： ctrl + shift + f
 * 24.选中数行，整体往后移动：tab
 * 25.选中数行，整体往前移动：shift + tab
 * 26.在当前类中，显示类结构，并支持搜索指定的方法、属性等：ctrl + o
 * 27.批量修改指定的变量名、方法名、类名等：alt + shift + r
 * 28.选中的结构的大小写的切换：变成大写： ctrl + shift + x
 * 29.选中的结构的大小写的切换：变成小写：ctrl + shift + y
 * 30.调出生成getter/setter/构造器等结构： alt + shift + s
 * 31.显示当前选择资源(工程 or 文件)的属性：alt + enter
 * 32.快速查找：参照选中的Word快速定位到下一个 ：ctrl + k
 * 33.关闭当前窗口：ctrl + w
 * 34.关闭所有的窗口：ctrl + shift + w
 * 35.查看指定的结构使用过的地方：ctrl + alt + g
 * 36.查找与替换：ctrl + f
 * 37.最大化当前的View：ctrl + m
 * 38.直接定位到当前行的首位：home
 * 39.直接定位到当前行的末位：end
```

## 面向对象的特征之二：继承性 why?

一、继承性的好处：

① 减少了代码的冗余，提高了代码的复用性

② 便于功能的扩展

③ 为之后多态性的使用，提供了前提

二、继承性的格式： `class A extends B{}`

A:子类、派生类、subclass

B:父类、超类、基类、superclass

2.1体现：一旦子类A继承父类B以后，子类A中就获取了父类B中声明的所有的属性和方法。特别的，父类中声明为private的属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构。只有因为封装性的影响，使得子类不能直接调用父类的结构而已。

2.2 子类继承父类以后，还可以声明自己特有的属性或方法：实现功能的拓展。子类和父类的关系，不同于子集和集合的关系。

extends：延展、扩展

三、Java中关于继承性的规定：

1.一个类可以被多个子类继承。

2.Java中类的单继承性：一个类只能有一个父类

3.子父类是相对的概念。

4.子类直接继承的父类，称为：直接父类。间接继承的父类称为：间接父类

5.子类继承父类以后，就获取了直接父类以及所有间接父类中声明的属性和方法

四、 1.如果我们没有显式的声明一个类的父类的话，则此类继承于java.lang.Object类

2.所有的java类（除java.lang.Object类之外）都直接或间接的继承于java.lang.Object类

3.意味着，所有的java类具有java.lang.Object类声明的功能。

# day12

## 方法的重写(override / overwrite)

1.重写：子类继承父类以后，可以对父类中同名同参数的方法，进行覆盖操作

2.应用：重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，实际执行的是子类重写父类的方法。

1. 重写的规定：

    方法的声明： 权限修饰符 返回值类型 方法名(形参列表) throws 异常的类型{}

约定俗称：子类中的叫重写的方法，父类中的叫被重写的方法

① 子类重写的方法的方法名和形参列表与父类被重写的方法的方法名和形参列表相同

② 子类重写的方法的权限修饰符不小于父类被重写的方法的权限修饰符

> 特殊情况：子类不能重写父类中声明为private权限的方法

③ 返回值类型：

> 父类被重写的方法的返回值类型是void，则子类重写的方法的返回值类型只能是void
>
> 父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A类的子类
>
> 父类被重写的方法的返回值类型是基本数据类型(比如：double)，则子类重写的方法的返回值类型必须是相同的基本数据类型(必须也是double)

④ 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型（具体放到异常处理时候讲）

子类和父类中的同名同参数的方法要么都声明为非static的（考虑重写），要么都声明为static的（不是重写）。

- 面试题：区分方法的重载与重写

## super关键字的使用

1.super理解为：父类的

2.super可以用来调用：属性、方法、构造器

3.super的使用：调用属性和方法

- 3.1 我们可以在子类的方法或构造器中。通过使用"super.属性"或"super.方法"的方式，显式的调用父类中声明的属性或方法。但是，通常情况下，我们习惯省略"super."
- 3.2 特殊情况：当子类和父类中定义了同名的属性时，我们要想在子类中调用父类中声明的属性，则必须显式的使用"super.属性"的方式，表明调用的是父类中声明的属性。
- 3.3 特殊情况：当子类重写了父类中的方法以后，我们想在子类的方法中调用父类中被重写的方法时，则必须显式的使用"super.方法"的方式，表明调用的是父类中被重写的方法。

4.super调用构造器

- 4.1 我们可以在子类的构造器中显式的使用"super(形参列表)"的方式，调用父类中声明的指定的构造器
- 4.2 "super(形参列表)"的使用，必须声明在子类构造器的首行！
- 4.3 我们在类的构造器中，针对于"this(形参列表)"或"super(形参列表)"只能二选一，不能同时出现
- 4.4 在构造器的首行，没有显式的声明"this(形参列表)"或"super(形参列表)"，则默认调用的是父类中空参的构造器：super()
- 4.5 在类的多个构造器中，至少有一个类的构造器中使用了"super(形参列表)"，调用父类中的构造器

## 子类对象实例化的全过程

1.从结果上来看：（继承性）

- 子类继承父类以后，就获取了父类中声明的属性或方法。
- 创建子类的对象，在堆空间中，就会加载所有父类中声明的属性。

2.从过程上来看：

- 当我们通过子类的构造器创建子类对象时，我们一定会直接或间接的调用其父类的构造器，进而调用父类的父类的构造器，...
- 直到调用了java.lang.Object类中空参的构造器为止。正因为加载过所有的父类的结构，所以才可以看到内存中有
- 父类中的结构，子类对象才可以考虑进行调用。

**明确**：虽然创建子类对象时，调用了父类的构造器，但是自始至终就创建过一个对象，即为new的子类对象

## 面向对象特征之三：多态性

1.理解多态性：可以理解为一个事物的多种形态。

2.何为多态性：

对象的多态性：父类的引用指向子类的对象（或子类的对象赋给父类的引用）

1. 多态的使用：虚拟方法调用

有了对象的多态性以后，我们在编译期，只能调用父类中声明的方法，但在运行期，我们实际执行的是子类重写父类的方法。

总结：编译，看左边；运行，看右边。

4.多态性的使用前提： ① 类的继承关系 ② 方法的重写

5.对象的多态性，只适用于方法，不适用于属性（编译和运行都看左边）

# day13

## instanceof的使用和向下转型

`x instanceof A`:检验x是否为类A的对象，返回值为boolean型

使用情境：为了避免在向下转型时出现ClassCastException的异常，我们在向下转型之前，先进行instanceof的判断，一旦返回true，就进行向下转型。如果返回false，不进行向下转型。

如果 a instanceof A返回true,则 a instanceof B也返回true.其中，类B是类A的父类。

**x不能是基本数据类型，只能是引用类型**

**x 为 null则永远是false**

- 多态的使用：当调用子父类同名同参数的方法时，实际执行的是子类重写父类的方法 ---虚拟方法调用
- 有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法的，但是由于变量声明为父类类型，导致编译时，只能调用父类中声明的属性和方法。子类特有的属性和方法不能调用。

如何才能调用子类特有的属性和方法？—— 向下转型：使用强制类型转换符。（`Man m1 = (Man)p2;`）

## java.lang.Object类

1.Object类是所有Java类的根父类

2.如果在类的声明中未使用extends关键字指明其父类，则默认父类为java.lang.Object类

3.Object类中的功能(属性、方法)就具有通用性。

- 属性：无
- 方法：equals() / toString() / getClass() /hashCode() / clone() / finalize() / wait() 、 notify()、notifyAll()

4.Object类只声明了一个空参的构造器

## equals()

一、回顾 == 的使用：

== ：运算符

1.可以使用在基本数据类型变量和引用数据类型变量中

2.如果比较的是基本数据类型变量：比较两个变量保存的数据是否相等。（不一定类型要相同）

如果比较的是引用数据类型变量：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体

补充： == 符号使用时，必须保证符号左右两边的变量类型一致。

二、equals()方法的使用：

1.是一个方法，而非运算符

2.只能适用于引用数据类型

3.Object类中equals()的定义：



```
public boolean equals(Object obj) {
    return (this == obj);
}
```

说明：Object类中定义的equals()和==的作用是相同的：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体

4.像String、Date、File、包装类等都重写了Object类中的equals()方法。重写以后，比较的不是两个引用的地址是否相同，而是比较两个对象的"实体内容"是否相同。

5.通常情况下，我们自定义的类如果使用equals()的话，也通常是比较两个对象的"实体内容"是否相同。那么，我们就需要对Object类中的equals()进行重写.

**重写的原则**：比较两个对象的实体内容是否相同

## object类中toString()的使用：

1.当我们输出一个对象的引用时，实际上就是调用当前对象的toString()

2.Object类中toString()的定义：



```
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
 }
```

3.像String、Date、File、包装类等都重写了Object类中的toString()方法。使得在调用对象的toString()时，返回"实体内容"信息

4.自定义类也可以重写toString()方法，当调用此方法时，返回对象的"实体内容"

## Java中的JUnit单元测试

（eclipse）步骤：

1.选中当前工程 - 右键选择：build path - add libraries - JUnit 4 - 下一步

2.创建Java类，进行单元测试。此时的Java类要求：① 此类是public的 ②此类提供公共的无参的构造器

3.此类中声明单元测试方法。此时的单元测试方法：方法的权限是public,没有返回值，没有形参

4.此单元测试方法上需要声明注解：@Test,并在单元测试类中导入：import org.junit.Test;

5.声明好单元测试方法以后，就可以在方法体内测试相关的代码。

6.写完代码以后，左键双击单元测试方法名，右键：run as - JUnit Test

说明：

- 1.如果执行结果没有任何异常：绿条
- 2.如果执行结果出现异常：红条

## 包装类

| 基本类型 | 对应的包装类 |
| :------: | :----------: |
|   byte   |     Byte     |
|  short   |    Short     |
|   int    |   Integer    |
|   long   |     Long     |
|  float   |    Float     |
|  double  |    Double    |
|   char   |  Character   |
| boolean  |   Boolean    |

1.java提供了8种基本数据类型对应的包装类，使得基本数据类型的变量具有类的特征

2.掌握的：基本数据类型、包装类、String三者之间的相互转换

**基本数据类型 --->包装类：调用包装类的构造器**



~~~ java
    public void test1(){
        int num1 = 10;
//      System.out.println(num1.toString());
        Integer in1 = new Integer(num1);
        System.out.println(in1.toString());

        Integer in2 = new Integer("123");
        System.out.println(in2.toString());

        //报异常

//      Integer in3 = new Integer("123abc");
        //      System.out.println(in3.toString());


        Float f1 = new Float(12.3f);
        Float f2 = new Float("12.3");
        System.out.println(f1);
        System.out.println(f2);

        Boolean b1 = new Boolean(true);
        Boolean b2 = new Boolean("TrUe");
        System.out.println(b2);
        Boolean b3 = new Boolean("true123");
        System.out.println(b3);//false

        //特别注意此处，分别是boolean和Boolean，都没定义的情况下一个返回false一个返回null
        Order order = new Order();
        System.out.println(order.isMale);//false
        System.out.println(order.isFemale);//null
    }
    
    static class Order {
        boolean isMale;
        Boolean isFemale;
    }
~~~



**基本数据类型:调用包装类Xxx的xxxValue()**

~~~ java
    public void test2(){
        Integer in1 = new Integer(12);
        int i1 = in1.intValue();
        System.out.println(i1 + 1);
        Float f1 = new Float(12.3);
        float f2 = f1.floatValue();
        System.out.println(f2 + 1);
    }
~~~



**JDK 5.0 新特性：自动装箱 与自动拆箱**：包装类与基本类型自动转换

~~~ java
    public void test3() {
        //int num1 = 10;
        //基本数据型-->包装类的对象
        //method(num1);
        //自动装箱：基本数据类型 ---&gt;包装类
        int num2 = 10;
        Integer in1 = num2;//自动装箱
        boolean b1 = true;
        Boolean b2 = b1;//自动装箱
        //自动拆箱：包装类---&gt;基本数据类型
        System.out.println(in1.toString());
        int num3 = in1;//自动拆箱
    }

    public void method(Object obj) {
        System.out.println(obj);
    }
~~~



**基本数据类型、包装类--->String类型：调用String重载的valueOf(Xxx xxx)**

~~~ java
    public void test4() {
        int num1 = 10;
        //方式1：连接运算
        String str1 = num1 + "";
        //方式2：调用String的valueOf(Xxx xxx)
        float f1 = 12.3f;
        String str2 = String.valueOf(f1);//"12.3"
        Double d1 = new Double(12.4);
        String str3 = String.valueOf(d1);
        System.out.println(str2);
        System.out.println(str3);//"12.4"
    }
~~~



**String类型 --->基本数据类型、包装类：调用包装类的parseXxx(String s)**

~~~ java
    public void test5() {
        String str1 = "123";
        //错误的情况：没有相关性
        //int num1 = (int)str1;
        //Integer in1 = (Integer)str1;
        //可能会报NumberFormatException
        int num2 = Integer.parseInt(str1);
        System.out.println(num2 + 1);

        String str2 = "true1";
        boolean b1 = Boolean.parseBoolean(str2);
        System.out.println(b1);
    }
~~~





**总结**



![img](https://gitee.com/gu097/note/raw/master/img/202110251920521.png)

**包装类面试题**

题1

[![img](https://gitee.com/gu097/note/raw/master/img/202110251920812.png)](https://images.cnblogs.com/cnblogs_com/kylinxxx/1675669/t_2006081655491591635314(1).png)



答案：第一题是1.0；第二题是1。 解析：`true ? new Integer(1) : new Double(2.0);`编译的时候，这段代码得保证true后面的数据类型一致，所以提升为Double

题2

~~~ java
    public void test3() {
        Integer i = new Integer(1);
        Integer j = new Integer(1);
        System.out.println(i == j);//false
        //Integer内部定义了IntegerCache结构，IntegerCache中定义了Integer[],
        //保存了从-128~127范围的整数。如果我们使用自动装箱的方式，给Integer赋值的范围在
        //-128~127范围内时，可以直接使用数组中的元素，不用再去new了。目的：提高效率
        Integer m = 1;
        Integer n = 1;
        System.out.println(m == n);//true
        Integer x = 128;//相当于new了一个Integer对象
        Integer y = 128;//相当于new了一个Integer对象
        System.out.println(x == y);//false
    }
~~~



## 包装类缓存区与比较

Integer内部定义了IntegerCache结构，IntegerCache中定义了Integer[],保存了从-128~127范围的整数。

如果我们使用自动装箱的方式，给Integer赋值的范围在-128~127范围内时，可以直接使用数组中的元素，不用再去new了。

其它类型也有类似的机制。

**同时，当基本类型与包装类型做比较运算时，包装类型会自动拆箱，最终比较的时xxxvalueOf()与基本数据类型的值，而非地址。但是当两个包装类型做比较运算时，默认做的是地址值对比，因为java中引用类型之间的对比比较的都是地址，但是，如果像以上所说，Integer范围在-128~127之间则是值的对比。**

目的：提高效率

举例：

~~~ java
        Integer i1=12;
        Integer i2=12;
        int i3=12;
        System.out.println(i1 == i2);
        System.out.println(i3==i1);

        System.out.println();

        int i4=128;
        Integer i5 = 128;
        Integer i6=128;
        System.out.println(i4 == i5);
        System.out.println(i5 == i6);
~~~

输出结果：

​	true

​	true

​	false

​	true





# day14

## static关键字的使用

1.static:静态的

2.static可以用来修饰：属性、方法、代码块、内部类

3.使用static修饰属性：静态变量（或类变量）

3.1 属性，按是否使用static修饰，又分为：静态属性 vs 非静态属性(实例变量)

实例变量：我们创建了类的多个对象，每个对象都独立的拥有一套类中的非静态属性。当修改其中一个对象中的非静态属性时，不会导致其他对象中同样的属性值的修改。

静态变量：我们创建了类的多个对象，多个对象共享同一个静态变量。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，是修改过了的。

3.2 static修饰属性的其他说明：

① 静态变量随着类的加载而加载。可以通过"类.静态变量"的方式进行调用

② 静态变量的加载要早于对象的创建。

③ 由于类只会加载一次，则静态变量在内存中也只会存在一份：存在方法区的静态域中。

④ 类：类变量（√） 实例变量（×）

对象：类变量（√） 实例变量（√）

3.3 静态属性举例：System.out; Math.PI;

4.使用static修饰方法：静态方法

① 随着类的加载而加载，可以通过"类.静态方法"的方式进行调用

②类：静态变量（√） 非静态变量（×）

对象：静态变量（√） 非静态变量（√）

③ 静态方法中，只能调用静态的方法或属性；非静态方法中，既可以调用非静态的方法或属性，也可以调用静态的方法或属性

1. static注意点：

5.1 在静态的方法内，不能使用this关键字、super关键字

5.2 关于静态属性和静态方法的使用，大家都从生命周期的角度去理解。

6.开发中，如何确定一个属性是否要声明为static的？

> 属性是可以被多个对象所共享的，不会随着对象的不同而不同的。
>
> 类中的常量也常常声明为static

开发中，如何确定一个方法是否要声明为static的？

> 操作静态属性的方法，通常设置为static的
>
> 工具类中的方法，习惯上声明为stati c的。 比如：Math、Arrays、Collections

## 单例设计模式：

1. 所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对某个类只能存在一个对象实例。
2. 如何实现？

饿汉式 vs 懒汉式

1. 区分饿汉式 和 懒汉式

饿汉式：

- 坏处：对象加载时间过长。
- 好处：饿汉式是线程安全的

懒汉式：

- 好处：延迟对象的创建。
- 目前的写法坏处：线程不安全。--->到多线程内容时，再修改

## main()方法的使用说明：

- \1. main()方法作为程序的入口
- \2. main()方法也是一个普通的静态方法
- \3. main()方法可以作为我们与控制台交互的方式。（之前：使用Scanner）

## 类的成员之四：代码块（或初始化块）

1.代码块的作用：用来初始化类、对象

2.代码块如果有修饰的话，只能使用static.

3.分类：静态代码块 vs 非静态代码块

4.静态代码块

> 内部可以有输出语句
>
> 随着类的加载而执行,而且只执行一次
>
> 作用：初始化类的信息
>
> 如果一个类中定义了多个静态代码块，则按照声明的先后顺序执行
>
> 静态代码块的执行要优先于非静态代码块的执行
>
> 静态代码块内只能调用静态的属性、静态的方法，不能调用非静态的结构

5.非静态代码块

> 内部可以有输出语句
>
> 随着对象的创建而执行
>
> 每创建一个对象，就执行一次非静态代码块
>
> 作用：可以在创建对象时，对对象的属性等进行初始化
>
> 如果一个类中定义了多个非静态代码块，则按照声明的先后顺序执行
>
> 非静态代码块内可以调用静态的属性、静态的方法，或非静态的属性、非静态的方法

对属性可以赋值的位置：

- ①默认初始化
- ②显式初始化/⑤在代码块中赋值
- ③构造器中初始化
- ④有了对象以后，可以通过"对象.属性"或"对象.方法"的方式，进行赋值

执行的先后顺序：① - ② / ⑤ - ③ - ④

## final关键字

final:最终的

1.final可以用来修饰的结构：类、方法、变量

2.final 用来修饰一个类:此类不能被其他类所继承。比如：String类、System类、StringBuffer类

3.final 用来修饰方法：表明此方法不可以被重写。比如：Object类中getClass();

4.final 用来修饰变量：此时的"变量"就称为是一个常量

4.1 final修饰属性：可以考虑赋值的位置有：显式初始化、代码块中初始化、构造器中初始化

4.2 final修饰局部变量：尤其是使用final修饰形参时，表明此形参是一个常量。当我们调用此方法时，给常量形参赋一个实参。一旦赋值以后，就只能在方法体内使用此形参，但不能进行重新赋值。



```
public void show(final int num){
    //num = 20;//编译不通过
    System.out.println(num);
}
//不可以在方法内赋值，只有在调用时赋值，如test.show(10);
```



static final 用来修饰属性：全局常量

**面试题：排错**



```
public class Something{
    public int addOne(final int x){
        return ++x;//  错误的，因为改变了x；
        //return x + 1;//正确的。未改变x；
    }
}
```

# day15

## abstract关键字的使用

1.abstract:抽象的

2.abstract可以用来修饰的结构：类、方法

3.abstract修饰类：抽象类

> 此类不能实例化
>
> 抽象类中一定有构造器，便于子类实例化时调用（涉及：子类对象实例化的全过程）
>
> 开发中，都会提供抽象类的子类，让子类对象实例化，完成相关的操作

4.abstract修饰方法：抽象方法

> 抽象方法只有方法的声明，没有方法体
>
> 包含抽象方法的类，一定是一个抽象类。反之，抽象类中可以没有抽象方法的。
>
> 若子类重写了父类中的所有的抽象方法后，此子类方可实例化；若子类没有重写父类中的所有的抽象方法，则此子类也是一个抽象类，需要使用abstract修饰

## abstract使用上的注意点：

1.abstract不能用来修饰：属性、构造器等结构

2.abstract不能用来修饰私有方法、静态方法、final的方法、final的类

## 接口的使用

1.接口使用interface来定义

2.Java中，接口和类是并列的两个结构

3.如何定义接口：定义接口中的成员

3.1 JDK7及以前：只能定义全局常量和抽象方法

> 全局常量：public static final的.但是书写时，可以省略不写
>
> 抽象方法：public abstract的

3.2 JDK8：除了定义全局常量和抽象方法之外，还可以定义静态方法、默认方法（略）

4.接口中不能定义构造器的！意味着接口不可以实例化

5.Java开发中，接口通过让类去实现(implements)的方式来使用.如果实现类覆盖了接口中的所有抽象方法，则此实现类就可以实例化；如果实现类没有覆盖接口中所有的抽象方法，则此实现类仍为一个抽象类

6.Java类可以实现多个接口 --->弥补了Java单继承性的局限性格式：class AA extends BB implements CC,DD,EE

7.接口与接口之间可以继承，而且可以多继承

8.接口的具体使用，体现多态性

9.接口，实际上可以看做是一种规范

面试题：抽象类与接口有哪些异同？

- 1.接口使用上也满足多态性
- 2.接口，实际上就是定义了一种规范
- 3.开发中，体会面向接口编程！

## 类的内部成员之五：内部类

1.Java中允许将一个类A声明在另一个类B中，则类A就是内部类，类B称为外部类

2.内部类的分类：成员内部类（静态、非静态） vs 局部内部类(方法内、代码块内、构造器内)

3.成员内部类：

一方面，作为外部类的成员：

> 调用外部类的结构
>
> 可以被static修饰
>
> 可以被4种不同的权限修饰

另一方面，作为一个类：

> 类内可以定义属性、方法、构造器等
>
> 可以被final修饰，表示此类不能被继承。言外之意，不使用final，就可以被继承
>
> 可以被abstract修饰

4.关注如下的3个问题

- 4.1 如何实例化成员内部类的对象

- 4.2 如何在成员内部类中区分调用外部类的结构

- 4.3 开发中局部内部类的使用 见《InnerClassTest1.java》

    

    ```
    //创建Dog实例(静态的成员内部类):
    Person.Dog dog = new Person.Dog();
    dog.show();
    //创建Bird实例(非静态的成员内部类):
    //Person.Bird bird = new Person.Bird();//错误的
    Person p = new Person();
    Person.Bird bird = p.new Bird();
    bird.sing();
    ```

# day16

## Error:

Java虚拟机无法解决的严重问题。如：JVM系统内部错误、资源耗尽等严重情况。比如：StackOverflowError和OOM。

一般不编写针对性的代码进行处理。

## java.lang.Throwable

- java.lang.Error:一般不编写针对性的代码进行处理。
- java.lang.Exception:可以进行异常的处理

## 编译时异常(checked)

> IOException
>
> > FileNotFoundException
>
> ClassNotFoundException

## 运行时异常(unchecked,RuntimeException)

> NullPointerException
>
> > ArrayIndexOutOfBoundsException
> >
> > ClassCastException
> >
> > NumberFormatException
> >
> > InputMismatchException
> >
> > ArithmeticException

## 一、异常的处理：抓抛模型

过程一："抛"：程序在正常执行的过程中，一旦出现异常，就会在异常代码处生成一个对应异常类的对象,并将此对象抛出。一旦抛出对象以后，其后的代码就不再执行。

关于异常对象的产生： ① 系统自动生成的异常对象 ② 手动的生成一个异常对象，并抛出（throw）

过程二："抓"：可以理解为异常的处理方式：① try-catch-finally ② throws

## 二、try-catch-finally的使用



```
try{
        //可能出现异常的代码
}catch(异常类型1 变量名1){
//处理异常的方式1
}catch(异常类型2 变量名2){
//处理异常的方式2
}catch(异常类型3 变量名3){
//处理异常的方式3
}
....
finally{
//一定会执行的代码
}
```



说明：

1.finally是可选的。

2.使用try将可能出现异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个对应异常类的对象，根据此对象的类型，去catch中进行匹配

3.一旦try中的异常对象匹配到某一个catch时，就进入catch中进行异常的处理。一旦处理完成，就跳出当前的try-catch结构（在没有写finally的情况）。继续执行其后的代码

4.catch中的异常类型如果没有子父类关系，则谁声明在上，谁声明在下无所谓。 catch中的异常类型如果满足子父类关系，则要求子类一定声明在父类的上面。否则，报错

5.常用的异常对象处理的方式： ① String getMessage() ② printStackTrace()

6.在try结构中声明的变量，再出了try结构以后，就不能再被调用

7.try-catch-finally结构可以嵌套

- 体会1：使用try-catch-finally处理编译时异常，是得程序在编译时就不再报错，但是运行时仍可能报错。相当于我们使用try-catch-finally将一个编译时可能出现的异常，延迟到运行时出现。
- 体会2：开发中，由于运行时异常比较常见，所以我们通常就不针对运行时异常编写try-catch-finally了。针对于编译时异常，我们说一定要考虑异常的处理。

## try-catch-finally中finally的使用：

1.finally是可选的

2.finally中声明的是一定会被执行的代码。即使catch中又出现异常了，try中有return语句，catch中有return语句等情况。

3.像数据库连接、输入输出流、网络编程Socket等资源，JVM是不能自动的回收的，我们需要自己手动的进行资源的释放。此时的资源释放，就需要声明在finally中。

## 异常处理的方式二：throws + 异常类型

1."throws + 异常类型"写在方法的声明处。指明此方法执行时，可能会抛出的异常类型。一旦当方法体执行时，出现异常，仍会在异常代码处生成一个异常类的对象，此对象满足throws后异常类型时，就会被抛出。异常代码后续的代码，就不再执行！

2.体会：try-catch-finally:真正的将异常给处理掉了。throws的方式只是将异常抛给了方法的调用者,并没有真正将异常处理掉。

3.开发中如何选择使用try-catch-finally 还是使用throws？

- 3.1 如果父类中被重写的方法没有throws方式处理异常，则子类重写的方法也不能使用throws，意味着如果子类重写的方法中有异常，必须使用try-catch-finally方式处理。
- 3.2 执行的方法a中，先后又调用了另外的几个方法，这几个方法是递进关系执行的。我们建议这几个方法使用throws的方式进行处理。而执行的方法a可以考虑使用try-catch-finally方式进行处理。

方法重写的规则之一： * 子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型

## 如何自定义异常类？

- \1. 继承于现有的异常结构：RuntimeException 、Exception
- \2. 提供全局常量：serialVersionUID
- \3. 提供重载的构造器



# day25

## Map接口

一、Map的实现类的结构：
|----Map:双列数据，存储key-value对的数据 ---类似于高中的函数：y = f(x)
　　　|----HashMap:作为Map的主要实现类；线程不安全的，效率高；存储null的key和value
　　　　　　|----LinkedHashMap:保证在遍历map元素时，可以按照添加的顺序实现遍历。
　　　　　　　　　原因：在原有的HashMap底层结构基础上，添加了一对指针，指向前一个和后一个元素。对于频繁的遍历操作，此类执行效率高于HashMap。
　　　|----TreeMap:保证按照添加的key-value对进行排序，实现排序遍历。此时考虑key的自然排序或定制排序，底层使用红黑树
　　　|----Hashtable:作为古老的实现类；线程安全的，效率低；不能存储null的key和value
　　　　　　|----Properties:常用来处理配置文件。key和value都是String类型

HashMap的底层：数组+链表 （jdk7及之前）
　　　　　　　　数组+链表+红黑树 （jdk 8）

面试题：

1. HashMap的底层实现原理？
2. HashMap 和 Hashtable的异同？
3. CurrentHashMap 与 Hashtable的异同？（暂时不讲）

二、Map结构的理解：

Map中的key:无序的、不可重复的，使用Set存储所有的key ---> key所在的类要重写equals()和hashCode() （以HashMap为例）

Map中的value:无序的、可重复的，使用Collection存储所有的value --->value所在的类要重写equals()

一个键值对：key-value构成了一个Entry对象。

Map中的entry:无序的、不可重复的，使用Set存储所有的entry

三、HashMap的底层实现原理？以jdk7为例说明：

```
HashMap map = new HashMap():
```

在实例化以后，底层创建了长度是16的一维数组Entry[] table。

...可能已经执行过多次put... ---> map.put(key1,value1):

首先，调用key1所在类的hashCode()计算key1哈希值，此哈希值经过某种算法计算以后，得到在Entry数组中的存放位置。

如果此位置上的数据为空，此时的key1-value1添加成功。 ----情况1

如果此位置上的数据不为空，(意味着此位置上存在一个或多个数据(以链表形式存在)),比较key1和已经存在的一个或多个数据的哈希值：

　　　如果key1的哈希值与已经存在的数据的哈希值都不相同，此时key1-value1添加成功。----情况2

　　　如果key1的哈希值和已经存在的某一个数据(key2-value2)的哈希值相同，继续比较：调用key1所在类的equals(key2)方法，比较：

　　　　　　如果equals()返回false:此时key1-value1添加成功。----情况3

　　　　　　如果equals()返回true:使用value1替换value2。

补充：关于情况2和情况3：此时key1-value1和原来的数据以链表的方式存储。

在不断的添加过程中，会涉及到扩容问题，当超出临界值(且要存放的位置非空)时，扩容。默认的扩容方式：扩容为原来容量的2倍，并将原有的数据复制过来。

jdk8 相较于jdk7在底层实现方面的不同：

1. new HashMap():底层没有创建一个长度为16的数组
2. jdk 8底层的数组是：Node[],而非Entry[]
3. 首次调用put()方法时，底层创建长度为16的数组
4. jdk7底层结构只有：数组+链表。jdk8中底层结构：数组+链表+红黑树。
    　　　4.1 形成链表时，七上八下（jdk7:新的元素指向旧的元素。jdk8：旧的元素指向新的元素）
    　　　4.2 当数组的某一个索引位置上的元素以链表形式存在的数据个数 > 8 且当前数组的长度 > 64时，此时此索引位置上的所数据改为使用红黑树存储。

DEFAULT_INITIAL_CAPACITY : HashMap的默认容量，16
DEFAULT_LOAD_FACTOR：HashMap的默认加载因子：0.75
threshold：扩容的临界值，=容量 * 填充因子：16 * 0.75 => 12
TREEIFY_THRESHOLD：Bucket中链表长度大于该默认值，转化为红黑树:8
MIN_TREEIFY_CAPACITY：桶中的Node被树化时最小的hash表容量:64

四、LinkedHashMap的底层实现原理（了解）

源码中：



```
static class Entry<K,V> extends HashMap.Node<K,V> {
     Entry<K,V> before, after;//能够记录添加的元素的先后顺序
     Entry(int hash, K key, V value, Node<K,V> next) {
        super(hash, key, value, next);
     }
 }
```

五、Map中定义的方法：

**添加、删除、修改操作：**

Object put(Object key,Object value)：将指定key-value添加到(或修改)当前map对象中
void putAll(Map m):将m中的所有key-value对存放到当前map中
Object remove(Object key)：移除指定key的key-value对，并返回value
void clear()：清空当前map中的所有数据

**元素查询的操作：**

Object get(Object key)：获取指定key对应的value
boolean containsKey(Object key)：是否包含指定的key
boolean containsValue(Object value)：是否包含指定的value
int size()：返回map中key-value对的个数
boolean isEmpty()：判断当前map是否为空
boolean equals(Object obj)：判断当前map和参数对象obj是否相等

**元视图操作的方法：**

Set keySet()：返回所有key构成的**Set集合**
Collection values()：返回所有value构成的**Collection集合**
Set entrySet()：返回所有key-value对构成的**Set集合**

①遍历所有的key集



```
//遍历所有的key集：keySet()
Set set = map.keySet();
Iterator iterator = set.iterator();
while(iterator.hasNext()){
    System.out.println(iterator.next());
}
```

②遍历所有的value集



```
//遍历所有的value集: values()
Collection values = map.values();
for(Object obj : values){
    System.out.println(obj);
}
```

③遍历所有的key-value



```
//遍历所有的key-value
//方式一：entrySet（）
Set entrySet = map.entrySet();
Iterator iterator1 = entrySet.iterator();
while(iterator1.hasNext()){
    Object obj = iterator1.next();
    //entrySet集合中的元素都是entry
    Map.Entry entry = (Map.Entry) obj;
    System.out.println(entry.getKey() + "------>" + entry.getValue());
}
System.out.println();
//方式二：
Set keySet = map.keySet();
Iterator iterator2 = keySet.iterator();
while(iterator2.hasNext()){
Object key = iterator2.next();
Object value = map.get(key);
System.out.println(key + "======" + value);
}
```



总结：常用方法：

*添加*：put(Object key,Object value)

*删除*：remove(Object key)

*修改*：put(Object key,Object value)

*查询*：get(Object key)

*长度*：size()

*遍历* ：keySet() / values() / entrySet()

## TreeSet

向TreeMap中添加key-value，要求key必须是由同一个类创建的对象

因为要按照key进行排序：自然排序 、定制排序

TreeSet排序例子





import org.junit.Test;



import java.util.*;



public class TreeMapTest {



```
//自然排序
@Test
public void test1(){
    TreeMap map = new TreeMap();
    User u1 = new User(&quot;Tom&quot;,23);
    User u2 = new User(&quot;Jerry&quot;,32);
    User u3 = new User(&quot;Jack&quot;,20);
    User u4 = new User(&quot;Rose&quot;,18);

    map.put(u1,98);
    map.put(u2,89);
    map.put(u3,76);
    map.put(u4,100);

    Set entrySet = map.entrySet();
    Iterator iterator1 = entrySet.iterator();
    while (iterator1.hasNext()){
        Object obj = iterator1.next();
        Map.Entry entry = (Map.Entry) obj;
        System.out.println(entry.getKey() + &quot;----&gt;&quot; + entry.getValue());

    }
}

//定制排序
@Test
public void test2(){
    TreeMap map = new TreeMap(new Comparator() {
        @Override
        public int compare(Object o1, Object o2) {
            if(o1 instanceof User &amp;&amp; o2 instanceof User){
                User u1 = (User)o1;
                User u2 = (User)o2;
                return Integer.compare(u1.getAge(),u2.getAge());
            }
            throw new RuntimeException(&quot;输入的类型不匹配！&quot;);
        }
    });
    User u1 = new User(&quot;Tom&quot;,23);
    User u2 = new User(&quot;Jerry&quot;,32);
    User u3 = new User(&quot;Jack&quot;,20);
    User u4 = new User(&quot;Rose&quot;,18);

    map.put(u1,98);
    map.put(u2,89);
    map.put(u3,76);
    map.put(u4,100);

    Set entrySet = map.entrySet();
    Iterator iterator1 = entrySet.iterator();
    while (iterator1.hasNext()){
        Object obj = iterator1.next();
        Map.Entry entry = (Map.Entry) obj;
        System.out.println(entry.getKey() + &quot;----&gt;&quot; + entry.getValue());

    }
}
```



}



## Collections：操作Collection、Map的工具类

reverse(List)：反转 List 中元素的顺序
shuffle(List)：对 List 集合元素进行随机排序
sort(List)：根据元素的自然顺序对指定 List 集合元素按升序排序
sort(List，Comparator)：根据指定的 Comparator 产生的顺序对 List 集合元素进行排序
swap(List，int， int)：将指定 list 集合中的 i 处元素和 j 处元素进行交换

Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素
Object max(Collection，Comparator)：根据 Comparator 指定的顺序，返回给定集合中的最大元素
Object min(Collection)
Object min(Collection，Comparator)
int frequency(Collection，Object)：返回指定集合中指定元素的出现次数
void copy(List dest,List src)：将src中的内容复制到dest中
boolean replaceAll(List list，Object oldVal，Object newVal)：使用新值替换 List 对象的所有旧值

其中要注意copy函数的使用：



```
//报异常：IndexOutOfBoundsException("Source does not fit in dest")
List dest = new ArrayList();
Collections.copy(dest,list);
```

正确的用法：



```
List dest = Arrays.asList(new Object[list.size()]);
System.out.println(dest.size());//list.size();
Collections.copy(dest,list);
System.out.println(dest);
```



Collections 类中提供了多个 synchronizedXxx() 方法，该方法可使将指定集合包装成线程同步的集合，从而可以解决多线程并发访问集合时的线程安全问题



```
//返回的list1即为线程安全的List
List list1 = Collections.synchronizedList(list);
```

## Properties

Properties:常用来处理配置文件。key和value都是String类型

例子





import java.io.FileInputStream;



import java.io.IOException;



import java.util.Properties;



public class PropertiesTest {



```
//Properties:常用来处理配置文件。key和value都是String类型
public static void main(String[] args)  {
    FileInputStream fis = null;
    try {
        Properties pros = new Properties();

        fis = new FileInputStream(&quot;jdbc.properties&quot;);
        pros.load(fis);//加载流对应的文件

        String name = pros.getProperty(&quot;name&quot;);
        String password = pros.getProperty(&quot;password&quot;);

        System.out.println(&quot;name = &quot; + name + &quot;, password = &quot; + password);
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if(fis != null){
            try {
                fis.close();
            } catch (IOException e) {
                e.printStackTrace();
            }

        }
    }

}
```



}



# day26

## 泛型的使用

1.jdk 5.0新增的特性

2.在集合中使用泛型：

以ArrayList为例：





@Test



publicvoid test1(){



​    ArrayList<Integer> list = new ArrayList<>();



```
list.add(78);
list.add(87);
list.add(99);
list.add(65);

//list.add(&quot;Tom&quot;);

Iterator&lt;Integer&gt; iterator = list.iterator();
while (iterator.hasNext()){
    System.out.println(iterator.next());
}
```



}



以HashSet为例





@Test



public void test2(){



```
Map&lt;String, Integer&gt; map = new HashMap&lt;&gt;();

map.put(&quot;Tom&quot;,87);
map.put(&quot;Jerry&quot;,87);
map.put(&quot;Jack&quot;,67);

//map.put(123, &quot;kkk&quot;);

//泛型的嵌套
Set&lt;Map.Entry&lt;String, Integer&gt;&gt; entry = map.entrySet();
Iterator&lt;Map.Entry&lt;String, Integer&gt;&gt; iterator = entry.iterator();
while(iterator.hasNext()){
    Map.Entry&lt;String, Integer&gt; e = iterator.next();
    String key = e.getKey();
    Integer value = e.getValue();
    System.out.println(key + &quot;-----&gt;&quot; + value);
}
```



}



总结：
① 集合接口或集合类在jdk5.0时都修改为带泛型的结构。
② 在实例化集合类时，可以指明具体的泛型类型
③ 指明完以后，在集合类或接口中凡是定义类或接口时，内部结构（比如：方法、构造器、属性等）使用到类的泛型的位置，都指定为实例化的泛型类型。
比如：add(E e) --->实例化以后：add(Integer e)
④ 注意点：泛型的类型必须是类，不能是基本数据类型。需要用到基本数据类型的位置，拿包装类替换
⑤ 如果实例化时，没有指明泛型的类型。默认类型为java.lang.Object类型。

3.如何自定义泛型结构：泛型类、泛型接口；泛型方法

如果定义了泛型类，实例化没有指明类的泛型，则认为此泛型类型为Object类型，**如果大家定义了类是带泛型的，建议在实例化时要指明类的泛型。**

定义一个继承了Order的子类，它的类型为





public class SubOrder extends Order<Integer> {



```
public static &lt;E&gt; List&lt;E&gt; copyFromArrayToList(E[] arr){
    ArrayList&lt;E&gt; list = new ArrayList&lt;&gt;();

    for (E e: arr){
        list.add(e);
    }

    return list;
}
```



}



那么，由于子类在继承带泛型的父类时，指明了泛型类型。则实例化子类对象时，不再需要指明泛型。



```
SubOrder sub1 = new SubOrder();
sub1.setOrderT(1122);
```

如果一个子类在继承时未声明类型：



```
public class SubOrder1<T> extends Order<T> {
}
```

声明时：



```
SubOrder1<String> sub2 = new SubOrder1<>();
sub2.setOrderT("order2......");
```

泛型不同的引用不能相互赋值。



```
ArrayList<String> list1 = null;
ArrayList<Integer> list2 = new ArrayList<>();
//泛型不同的引用不能相互赋值。
//list1 = list2;
```

说明：
\1. 泛型类可能有多个参数，此时应将多个参数一起放在尖括号内。比如：`< E1,E2,E3>`
\2. 泛型类的构造器如下 `public GenericClass(){}` 。而下面是错误的`public GenericClass<E>(){}` 3. 实例化后，操作原来泛型位置的结构必须与指定的泛型类型一致。
\4. 泛型不同的引用不能相互赋值。尽管在编译时 ArrayList 和 ArrayList 是两种类型，但是，在运行时只有一个 ArrayList 被加载到 JVM 中。
\5. 泛型如果不指定，将被擦除，泛型对应的类型均按照 Object 处理，但不等价于Object。**经验： 泛型要使用一路都用。要不用，一路都不要用。**
\6. 如果泛型结构是一个接口或抽象类，则不可创建泛型类的对象 。
\7. jdk1.7，泛型的简化 操作 `ArrayList<Fruit> flist = new ArrayList<>();`
\8. 泛型的指定中不能使用基本数据类型，可以使用包装类替换。
\9. 在类接口上声明的泛型，在本类或本接口中即代表某种类型，可以作为非静态属性的类型、非静态方法的参数类型、非静态方法的返回值类型。**但在静态方法中不能使用类的泛型。**
\10. 异常类不能是泛型的
\11. 不能使用 `new E[]` 。但是可以 `E[] elements = (E[])new Object[capacity];`
参考：ArrayList 源码中声明： `Object[] elementData` 而非泛型参数类型数组。
\12. 父类有泛型，子类可以选择保留泛型也可以选择指定泛型类型：

子类不保留父类的泛型：按需实现

　　没有类型 擦除

　　具体类型

子类保留父类的泛型：泛型子类

　　全部保留

　　部分保留

结论：子类必须是“富二代”，子类除了指定或保留父类的泛型，还可以增加自 己的泛型

## 泛型方法

泛型方法的格式： [访问权限] <泛型> 返回类型 方法名 ([泛型标识 参数名称]) 抛出的异常

## 泛型在继承方面的体现

虽然类A是类B的父类，但是G<A>和G<B>二者不具备子父类关系，二者是并列关系。

补充：类A是类B的父类，A<G> 是 B<G> 的父类

## 通配符的使用

通配符：?

类A是类B的父类，G<A>和G<B>是没有关系的，二者共同的父类是：G<?>





@Test



publicvoid test1(){



List<Object> list1 = null;



List<String> list2 = null;



```
List&lt;?&gt; list = null;

list = list1;
list = list2;

System.out.println(list1);
System.out.println(list2);


List&lt;String&gt; list3 = new ArrayList&lt;&gt;();
list3.add(&quot;ASA&quot;);
list3.add(&quot;DGA&quot;);
list3.add(&quot;Gesag&quot;);

//list.add(&quot;AA&quot;);
//list.add('?');

list.add(null);

//获取(读取)：允许读取数据，读取的数据类型为Object。
Object o = list.get(0);
System.out.println(o);
```







分析：

因为？是两者的共同父类，所以可以将list1和2传递给list

添加（写入）：对于List<?>就不能向其内部添加数据。除了null

读取：允许读取数据，读取的数据类型为Object。

## 有限制条件的通配符的使用。

? extends A:
　　　　G<? extends A> 可以作为G<A>和G<B>的父类，其中B是A的子类

? super A:
　　　　G<? super A> 可以作为G<A>和G<B>的父类，其中B是A的父类





@Test



public void test4(){



```
List&lt;? extends Person&gt; list1 = null;
List&lt;? super Person&gt; list2 = null;

List&lt;Student&gt; list3 = new ArrayList&lt;Student&gt;();
List&lt;Person&gt; list4 = new ArrayList&lt;Person&gt;();
List&lt;Object&gt; list5 = new ArrayList&lt;Object&gt;();

list1 = list3;
list1 = list4;
//list1 = list5;

//list2 = list3;
list2 = list4;
list2 = list5;

//读取数据：
list1 = list3;
Person p = list1.get(0);
//编译不通过
//Student s = list1.get(0);

list2 = list4;
Object obj = list2.get(0);
////编译不通过
//Person obj = list2.get(0);

//写入数据：
//编译不通过
//list1.add(new Student());

//编译通过
list2.add(new Person());
list2.add(new Student());
```



}



## File类的使用

1. File类的一个对象，代表一个文件或一个文件目录(俗称：文件夹)
2. File类声明在java.io包下
3. File类中涉及到关于文件或文件目录的创建、删除、重命名、修改时间、文件大小等方法，并未涉及到写入或读取文件内容的操作。如果需要读取或写入文件内容，必须使用IO流来完成。
4. 后续File类的对象常会作为参数传递到流的构造器中，指明读取或写入的"终点".

如何创建File类的实例



```
File(String filePath)
File(String parentPath,String childPath)
File(File parentFile,String childPath)
```

> 相对路径：相较于某个路径下，指明的路径。
> 绝对路径：包含盘符在内的文件或文件目录的路径

路径分隔符



```
 windows:\\
 unix:/
 */
```

public String getAbsolutePath()：获取绝对路径
public String getPath() ：获取路径
public String getName() ：获取名称
public String getParent()：获取上层文件目录路径。若无，返回null
public long length() ：获取文件长度（即：字节数）。不能获取目录的长度。
public long lastModified() ：获取最后一次的修改时间，毫秒值

如下的两个方法适用于文件目录：
public String[] list() ：获取指定目录下的所有文件或者文件目录的名称数组
public File[] listFiles() ：获取指定目录下的所有文件或者文件目录的File数组

------

public boolean renameTo(File dest):把文件重命名为指定的文件路径
比如：file1.renameTo(file2)为例：
要想保证返回true,需要file1在硬盘中是存在的，且file2不能在硬盘中存在。

------

public boolean isDirectory()：判断是否是文件目录
public boolean isFile() ：判断是否是文件
public boolean exists() ：判断是否存在
public boolean canRead() ：判断是否可读
public boolean canWrite() ：判断是否可写
public boolean isHidden() ：判断是否隐藏

------

创建硬盘中对应的文件或文件目录

public boolean createNewFile() ：创建文件。若文件存在，则不创建，返回false
public boolean mkdir() ：创建文件目录。如果此文件目录存在，就不创建了。如果此文件目录的上层目录不存在，也不创建。
public boolean mkdirs() ：创建文件目录。如果此文件目录存在，就不创建了。如果上层文件目录不存在，一并创建

删除磁盘中的文件或文件目录

public boolean delete()：删除文件或者文件夹
**删除注意事项：Java中的删除不走回收站。**

要想删除成功，io4文件目录下不能有子目录或文件

# day27

## 流

一、流的分类：
1.操作数据单位：字节流、字符流
2.数据的流向：输入流、输出流
3.流的角色：节点流、处理流

| 抽象基类 | 字节流       | 字符流 |
| :------- | :----------- | :----- |
| 输入流   | InputStream  | Reader |
| 输出流   | OutputStream | Writer |

[![img](https://gitee.com/gu097/note/raw/master/img/202110251920581.png)](https://images.cnblogs.com/cnblogs_com/kylinxxx/1675669/o_2007121432391594564335(1).png)

二、流的体系结构

| 抽象基类     | 节点流（或文件流）                          | 缓冲流（处理流的一种）                                     |
| :----------- | :------------------------------------------ | :--------------------------------------------------------- |
| InputStream  | FileInputStream(read(byte[] buffer))        | BufferedInputStream (read(byte[] buffer))                  |
| OutputStream | FileOutputStream(write(byte[] buffer,0,len) | BufferedOutputStream (write(byte[] buffer,0,len) / flush() |
| Reader       | FileReader (read(char[] cbuf))              | BufferedReader (read(char[] cbuf) / readLine())            |
| Writer       | FileWriter (write(char[] cbuf,0,len)        | BufferedWriter (write(char[] cbuf,0,len) / flush()         |

说明点：
\1. read()的理解：返回读入的一个字符。如果达到文件末尾，返回-1
\2. 异常的处理：为了保证流资源一定可以执行关闭操作。需要使用try-catch-finally处理
\3. 读入的文件一定要存在，否则就会报FileNotFoundException。

学会对read（）操作升级：使用read的重载方法

示例代码：

```
@Test
publicvoidtestFileReader1(){
	FileReader fr = null;
	try{
	//1.File类的实例化
File file = new File("hello.txt");
//2.FileReader流的实例化
fr = new FileReader(file);
    //3. 读入的操作
    //read(char[] cbuf):返回每次读入cbuf数组中的字符的个数。如果大奥文件末尾，返回-1
    char[] cbuf = new char[5];
    int len;
    while((len = fr.read(cbuf)) != -1){
        String str = new String(cbuf, 0 ,len);
        System.out.println(str);
    }

}catch (IOException e){
    e.printStackTrace();
}finally {
    if(fr != null){
        try {
            fr.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```



}



读取文件的推荐方式：



```
while((len = fr.read(cbuf)) != -1){
    String str = new String(cbuf, 0 ,len);
    System.out.println(str);
}
```

从内存中写出数据到硬盘的文件里。

说明：
\1. 输出操作，对应的File可以不存在的。并不会报异常
\2. File对应的硬盘中的文件如果不存在，在输出的过程中，会自动创建此文件。
File对应的硬盘中的文件如果存在：
如果流使用的构造器是：FileWriter(file,false) / FileWriter(file):对原有文件的覆盖
如果流使用的构造器是：FileWriter(file,true):不会对原有文件覆盖，而是在原有文件基础上追加内容

IO流基本操作：
1.File类的实例化
2.FileReader流的实例化
3.读入的操作
4.资源的关闭

------

read():返回读入的一个字符。如果达到文件末尾，返回-1

不能使用字符流来处理图片等字节数据

## 测试FileInputStream和FileOutputStream的使用

1. 对于文本文件(.txt,.java,.c,.cpp)，使用字符流处理
2. 对于非文本文件(.jpg,.mp3,.mp4,.avi,.doc,.ppt,...)，使用字节流处理

使用字节流FileInputStream处理文本文件，可能出现乱码。

图片复制操作示例代码





/* 实现对图片的复制操作 */



@Test



publicvoidtestFileInputOutputStream()  {



​    FileInputStream fis = null;



​    FileOutputStream fos = null;



try {



//



​        File srcFile = new File("爱情与友情.jpg");



​        File destFile = new File("爱情与友情2.jpg");



```
    //
    fis = new FileInputStream(srcFile);
    fos = new FileOutputStream(destFile);

    //复制的过程
    byte[] buffer = new byte[5];
    int len;
    while((len = fis.read(buffer)) != -1){
        fos.write(buffer,0,len);
    }

} catch (IOException e) {
    e.printStackTrace();
} finally {
    if(fos != null){
        //
        try {
            fos.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    if(fis != null){
        try {
            fis.close();
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
}
```



}



## 处理流之一：缓冲流的使用

1.缓冲流：

- BufferedInputStream
- BufferedOutputStream
- BufferedReader
- BufferedWriter

2.作用：提供流的读取、写入的速度

提高读写速度的原因：内部提供了一个缓冲区

3.处理流，就是“套接”在已有的流的基础上。

说明：

① 关闭外层流的同时，内层流也会自动的进行关闭。关于内层流的关闭，我们可以省略.

② 使用String读取数据：



```
//方式二：使用String
String data;
while((data = br.readLine()) != null){
    //方法一：
    //bw.write(data + "\n");//data中不包含换行符
    //方法二：
    bw.write(data);//data中不包含换行符
    bw.newLine();//提供换行的操作
}
```

复制文件的示例代码：





//实现文件复制的方法



publicvoidcopyFileWithBuffered(String srcPath,String destPath){



​    BufferedInputStream bis = null;



​    BufferedOutputStream bos = null;



```
try {
    //1.造文件
    File srcFile = new File(srcPath);
    File destFile = new File(destPath);
    //2.造流
    //2.1 造节点流
    FileInputStream fis = new FileInputStream((srcFile));
    FileOutputStream fos = new FileOutputStream(destFile);
    //2.2 造缓冲流
    bis = new BufferedInputStream(fis);
    bos = new BufferedOutputStream(fos);

    //3.复制的细节：读取、写入
    byte[] buffer = new byte[1024];
    int len;
    while((len = bis.read(buffer)) != -1){
        bos.write(buffer,0,len);
    }
} catch (IOException e) {
    e.printStackTrace();
} finally {
    //4.资源关闭
    //要求：先关闭外层的流，再关闭内层的流
    if(bos != null){
        try {
            bos.close();
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
    if(bis != null){
        try {
            bis.close();
        } catch (IOException e) {
            e.printStackTrace();
        }

    }
    //说明：关闭外层流的同时，内层流也会自动的进行关闭。关于内层流的关闭，我们可以省略.
//fos.close();
//fis.close();
}
```



}



## 处理流之二：转换流的使用

1.转换流：属于字符流

- InputStreamReader：将一个字节的输入流转换为字符的输入流
- OutputStreamWriter：将一个字符的输出流转换为字节的输出流

2.作用：提供字节流与字符流之间的转换



```
//参数2指明了字符集，具体使用哪个字符集，取决于文件dbcp.txt保存时使用的字符集  
InputStreamReader isr = new InputStreamReader(fis,"UTF-8");
```

3.解码：字节、字节数组 --->字符数组、字符串
编码：字符数组、字符串 ---> 字节、字节数组

4.字符集

- ASCII：美国标准信息交换码。用一个字节的7位可以表示。
- ISO8859-1：拉丁码表。欧洲码表。用一个字节的8位表示。
- GB2312：中国的中文编码表。最多两个字节编码所有字符
- GBK：中国的中文编码表升级，融合了更多的中文文字符号。最多两个字节编码
- Unicode：国际标准码，融合了目前人类使用的所有字符。为每个字符分配唯一的字符码。所有的文字都用两个字节来表示。
- UTF-8：变长的编码方式，可用1-4个字节来表示一个字符。

示例代码：





/* 此时处理异常的话，仍然应该使用try-catch-finally

综合使用InputStreamReader和OutputStreamWriter
 */
 @Test
 public void test2() throws Exception {
 [//1.造文件](https://1.xn--5nqy36cy93a/)、造流
 File file1 = new File("dbcp.txt");
 File file2 = new File("dbcp_gbk.txt");



```
FileInputStream fis = new FileInputStream(file1);
FileOutputStream fos = new FileOutputStream(file2);

InputStreamReader isr = new InputStreamReader(fis,&quot;utf-8&quot;);
OutputStreamWriter osw = new OutputStreamWriter(fos,&quot;gbk&quot;);

//2.读写过程
char[] cbuf = new char[20];
int len;
while((len = isr.read(cbuf)) != -1){
    osw.write(cbuf,0,len);
}

//3.关闭资源
isr.close();
osw.close();
```



}



# day28

## Path

1. jdk 7.0 时，引入了 Path、Paths、Files三个类。

2. 此三个类声明在：java.nio.file包下。

3. Path可以看做是java.io.File类的升级版本。也可以表示文件或文件目录，与平台无关

4. 如何实例化Path:使用Paths.

    `static Path get(String first, String … more)` : 用于将多个字符串串连成路径
    `static Path get(URI uri)`: 返回指定uri对应的Path路径

**如何使用Paths实例化Path**

示例代码：





@Test



public void test1() {



​    Path path1 = Paths.get("d:\\nio\\hello.txt");//new File(String filepath)



```
Path path2 = Paths.get(&quot;d:\\&quot;, &quot;nio\\hello.txt&quot;);//new File(String parent,String filename);

System.out.println(path1);
System.out.println(path2);

Path path3 = Paths.get(&quot;d:\\&quot;, &quot;nio&quot;);
System.out.println(path3);
```



}



**Path中的常用方法**

`String toString()` ： 返回调用 Path 对象的字符串表示形式
`boolean startsWith(String path)` : 判断是否以 path 路径开始
`boolean endsWith(String path)` : 判断是否以 path 路径结束
`boolean isAbsolute()` : 判断是否是绝对路径
`Path getParent()`：返回Path对象包含整个路径，不包含 Path 对象指定的文件路径
`Path getRoot()` ：返回调用 Path 对象的根路径
`Path getFileName()` : 返回与调用 Path 对象关联的文件名
`int getNameCount()`: 返回Path 根目录后面元素的数量
`Path getName(int idx)`: 返回指定索引位置 idx 的路径名称
`Path toAbsolutePath()` : 作为绝对路径返回调用 Path 对象
`Path resolve(Path p)` :合并两个路径，返回合并后的路径对应的Path对象
`File toFile()`: 将Path转化为File类的对象



```
File file = path1.toFile();//Path--->File的转换
Path newPath = file.toPath();//File--->Path的转换
```

## Files工具类的使用：操作文件或目录的工具类

以这两条代码为例，导入文件路径：



```
Path path1 = Paths.get("d:\\nio", "hello.txt");
Path path2 = Paths.get("atguigu.txt");
```

`Path copy(Path src, Path dest, CopyOption … how)`: 文件的复制
说明：要想复制成功，要求path1对应的物理上的文件存在。path1对应的文件没有要求。



```
Files.copy(path1, path2, StandardCopyOption.REPLACE_EXISTING);
```

`Path createDirectory(Path path, FileAttribute<?> … attr)` : 创建一个目录
说明：要想执行成功，要求path对应的物理上的文件目录不存在。一旦存在，抛出异常。



```
Path path3 = Paths.get("d:\\nio\\nio1");
Files.createDirectory(path3);
```

`Path createFile(Path path, FileAttribute<?> … arr)` : 创建一个文件
说明：要想执行成功，要求path对应的物理上的文件不存在。一旦存在，抛出异常。



```
Path path4 = Paths.get("d:\\nio\\hi.txt");
Files.createFile(path4);
```

`void delete(Path path)` : 删除一个文件/目录，如果不存在，执行报错



```
Files.delete(path4);
```

`void deleteIfExists(Path path)`: Path对应的文件/目录如果存在，执行删除.如果不存在，正常执行结束



```
Files.deleteIfExists(path3);
```

`Path move(Path src, Path dest, CopyOption…how)`: 将 src 移动到 dest 位置
说明：要想执行成功，src对应的物理上的文件需要存在，dest对应的文件没有要求。



```
Files.move(path1, path2, StandardCopyOption.ATOMIC_MOVE);
```

`long size(Path path)`: 返回 path 指定文件的大小



```
long size = Files.size(path2);
System.out.println(size);
```

`boolean exists(Path path, LinkOption … opts)`: 判断文件是否存在



```
System.out.println(Files.exists(path2, LinkOption.NOFOLLOW_LINKS));
```

`boolean isDirectory(Path path, LinkOption … opts)` : 判断是否是目录
说明：不要求此path对应的物理文件存在。



```
System.out.println(Files.isDirectory(path1, LinkOption.NOFOLLOW_LINKS));
```

`boolean isRegularFile(Path path, LinkOption … opts)` : 判断是否是文件

`boolean isHidden(Path path)` : 判断是否是隐藏文件
说明：要求此path对应的物理上的文件需要存在。才可判断是否隐藏。否则，抛异常。



```
System.out.println(Files.isHidden(path1));
```

`boolean isReadable(Path path)` : 判断文件是否可读



```
System.out.println(Files.isReadable(path1));
```

`boolean isWritable(Path path)` : 判断文件是否可写



```
System.out.println(Files.isWritable(path1));
```

`boolean notExists(Path path, LinkOption … opts)`: 判断文件是否不存在



```
System.out.println(Files.notExists(path1, LinkOption.NOFOLLOW_LINKS));
```

- StandardOpenOption.READ:表示对应的Channel是可读的。
- StandardOpenOption.WRITE：表示对应的Channel是可写的。
- StandardOpenOption.CREATE：如果要写出的文件不存在，则创建。如果存在，忽略
- StandardOpenOption.CREATE_NEW：如果要写出的文件不存在，则创建。如果存在，抛异常

`InputStream newInputStream(Path path, OpenOption…how)`:获取 InputStream 对象



```
InputStream inputStream = Files.newInputStream(path1, StandardOpenOption.READ);
```

`OutputStream newOutputStream(Path path, OpenOption…how)`: 获取 OutputStream 对象



```
OutputStream outputStream = Files.newOutputStream(path1, StandardOpenOption.WRITE,StandardOpenOption.CREATE);
```

`SeekableByteChannel newByteChannel(Path path, OpenOption…how)` : 获取与指定文件的连接，how 指定打开方式。



```
SeekableByteChannel channel = Files.newByteChannel(path1, StandardOpenOption.READ,StandardOpenOption.WRITE,StandardOpenOption.CREATE);
```

`DirectoryStream<Path> newDirectoryStream(Path path)` : 打开 path 指定的目录



```
Path path2 = Paths.get("e:\\teach");
DirectoryStream<Path> directoryStream = Files.newDirectoryStream(path2);
Iterator<Path> iterator = directoryStream.iterator();
while(iterator.hasNext()){
    System.out.println(iterator.next());
}
```

## 对象流的使用

1.ObjectInputStream 和 ObjectOutputStream
2.作用：用于存储和读取基本数据类型数据或对象的处理流。它的强大之处就是可以把Java中的对象写入到数据源中，也能把对象从数据源中还原回来。
3.要想一个java对象是可序列化的，需要满足相应的要求。见Person.java

Person.java





import java.io.Serializable;



/**



- 

- 

    Person需要满足如下的要求，方可序列化

    

- 

- 

    1.需要实现接口：Serializable

    

- 

- 

    2.当前类提供一个全局常量：serialVersionUID

    

- 

- 

    3.除了当前Person类需要实现Serializable接口之外，还必须保证其内部所有属性

    

- 

- 

    也必须是可序列化的。（默认情况下，基本数据类型可序列化）

    

- 

- 

- 

- 

- 

- 

    补充：ObjectOutputStream和ObjectInputStream不能序列化static和transient修饰的成员变量

    

- 

- 

- 

- 

- 

- 

    @author shkstart

    

- 

- 

    @create 2019 上午 10:38
     */
     public class Person implements Serializable{

    

    public static final long serialVersionUID = 475463534532L;

    

    private String name;
     private int age;
     private int id;
     private Account acct;

    

    public Person(String name, int age, int id) {
     this.name = name;
     this.age = age;
     this.id = id;
     }

    

    public Person(String name, int age, int id, Account acct) {
     this.name = name;
     this.age = age;
     this.id = id;
     this.acct = acct;
     }

    

    @Override
     public String toString() {
     return "Person{" +
     "name='" + name + ''' +
     ", age=" + age +
     ", id=" + id +
     ", acct=" + acct +
     '}';
     }

    

    public int getId() {
     return id;
     }

    

    public void setId(int id) {
     this.id = id;
     }

    

    public String getName() {
     return name;
     }

    

    public void setName(String name) {
     this.name = name;
     }

    

    public int getAge() {
     return age;
     }

    

    public void setAge(int age) {
     this.age = age;
     }

    

    public Person(String name, int age) {

    

    ```
     this.name = name;
     this.age = age;
    ```

    

    }

    

    public Person() {

    

    }
     }

    

- 



class Account implements Serializable{
 public static final long serialVersionUID = 4754534532L;
 private double balance;



```
@Override
public String toString() {
    return &quot;Account{&quot; +
            &quot;balance=&quot; + balance +
            '}';
}

public double getBalance() {
    return balance;
}

public void setBalance(double balance) {
    this.balance = balance;
}

public Account(double balance) {

    this.balance = balance;
}
```



}



4.序列化机制：
对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。

## RandomAccessFile的使用

1. RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口
2. RandomAccessFile既可以作为一个输入流，又可以作为一个输出流
3. 如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。如果写出到的文件存在，则会对原有文件内容进行覆盖。（默认情况下，从头覆盖）
4. 可以通过相关的操作，实现RandomAccessFile“插入”数据的效果

示例代码：





/* 使用RandomAccessFile实现数据的插入效果 */



@Test



public void test3() throws IOException {



```
RandomAccessFile raf1 = new RandomAccessFile(&quot;hello.txt&quot;,&quot;rw&quot;);

raf1.seek(3);//将指针调到角标为3的位置
//保存指针3后面的所有数据到StringBuilder中
StringBuilder builder = new StringBuilder((int) new File(&quot;hello.txt&quot;).length());
byte[] buffer = new byte[20];
int len;
while((len = raf1.read(buffer)) != -1){
    builder.append(new String(buffer,0,len)) ;
}
//调回指针，写入“xyz”
raf1.seek(3);
raf1.write(&quot;xyz&quot;.getBytes());

//将StringBuilder中的数据写入到文件中
raf1.write(builder.toString().getBytes());

raf1.close();
```



}



## 网络编程

一、网络编程中有两个主要的问题：

- 1.如何准确地定位网络上一台或多台主机；定位主机上的特定的应用
- 2.找到主机后如何可靠高效地进行数据传输

二、网络编程中的两个要素：

- 1.对应问题一：IP和端口号
- 2.对应问题二：提供网络通信协议：TCP/IP参考模型（应用层、传输层、网络层、物理+数据链路层）

三、通信要素一：IP和端口号

1.IP:唯一的标识 Internet 上的计算机（通信实体）
2.在Java中使用InetAddress类代表IP
3.IP分类：IPv4 和 IPv6 ; 万维网 和 局域网
4.域名:　　www.baidu.com　　www.mi.com　　www.sina.com　　www.jd.com　　www.vip.com
5.本地回路地址：127.0.0.1 对应着：localhost
6.如何实例化InetAddress:两个方法：getByName(String host) 、 getLocalHost()

　　两个常用方法：getHostName() / getHostAddress()

7.端口号：正在计算机上运行的进程。

- 要求：不同的进程有不同的端口号
- 范围：被规定为一个 16 位的整数 0~65535。

8.端口号与IP地址的组合得出一个网络套接字：Socket

## TCP的3个例子

通过三个例子学习客户端与服务端的交互

例子1： 客户端发送信息给服务端，服务端将数据显示在控制台上





publicclass TCPTest1 {



```
//客户端
@Test
public void client()  {
    Socket socket = null;
    OutputStream os = null;
    try {
        //1.创建Socket对象，指明服务器端的ip和端口号
        InetAddress inet = InetAddress.getByName(&quot;192.168.14.100&quot;);
        socket = new Socket(inet,8899);
        //2.获取一个输出流，用于输出数据
        os = socket.getOutputStream();
        //3.写出数据的操作
        os.write(&quot;你好，我是客户端mm&quot;.getBytes());
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        //4.资源的关闭
        if(os != null){
            try {
                os.close();
            } catch (IOException e) {
                e.printStackTrace();
            }

        }
        if(socket != null){
            try {
                socket.close();
            } catch (IOException e) {
                e.printStackTrace();
            }

        }
    }

}
//服务端
@Test
public void server()  {

    ServerSocket ss = null;
    Socket socket = null;
    InputStream is = null;
    ByteArrayOutputStream baos = null;
    try {
        //1.创建服务器端的ServerSocket，指明自己的端口号
        ss = new ServerSocket(8899);
        //2.调用accept()表示接收来自于客户端的socket
        socket = ss.accept();
        //3.获取输入流
        is = socket.getInputStream();

        //不建议这样写，可能会有乱码
```



//        byte[] buffer = new byte[1024];
 //        int len;
 //        while((len = is.read(buffer)) != -1){
 //            String str = new String(buffer,0,len);
 //            System.out.print(str);
 //        }
 [//4.读取输入流中的数据](https://4.xn--fiq41fttck5zolc8triyp4p4bv0g/)
 baos = new ByteArrayOutputStream();
 byte[] buffer = new byte[5];
 int len;
 while((len = is.read(buffer)) != -1){
 baos.write(buffer,0,len);
 }



```
        System.out.println(baos.toString());

        System.out.println(&quot;收到了来自于：&quot; + socket.getInetAddress().getHostAddress() + &quot;的数据&quot;);

    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        if(baos != null){
            //5.关闭资源
            try {
                baos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if(is != null){
            try {
                is.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if(socket != null){
            try {
                socket.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if(ss != null){
            try {
                ss.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }

    }

}
```



}



总结：
客户端步骤分为：

1. 创建Socket对象，指明服务器端的ip和端口号（关键字： Socket、InetAddress、getByName)
2. 获取一个输出流，用于输出数据（关键字： OutputStream、 socket.getOutputStream）
3. 写出数据的操作（关键字： getBytes）
4. 关闭资源（后用先关，先关输出流，再关socket）

服务端步骤分为：

1. 创建服务器端的ServerSocket，指明自己的端口号（关键字： ServerSocket）
2. 调用accept()表示接收来自于客户端的socket（关键字： accept）
3. 获取输入流（关键字： getInputStream）
4. **读取**输入流中的数据（关键字： ByteArrayOutputStream）
5. 关闭资源

例子2：客户端发送文件给服务端，服务端将文件保存在本地。





publicclassTCPTest2 {



```
/*
这里涉及到的异常，应该使用try-catch-finally处理
 */
@Test
public void client() throws IOException {
    //1.
    Socket socket = new Socket(InetAddress.getByName(&quot;127.0.0.1&quot;),9090);
    //2.
    OutputStream os = socket.getOutputStream();
    //3.
    FileInputStream fis = new FileInputStream(new File(&quot;beauty.jpg&quot;));
    //4.
    byte[] buffer = new byte[1024];
    int len;
    while((len = fis.read(buffer)) != -1){
        os.write(buffer,0,len);
    }
    //5.
    fis.close();
    os.close();
    socket.close();
}

/*
这里涉及到的异常，应该使用try-catch-finally处理
 */
@Test
public void server() throws IOException {
    //1.
    ServerSocket ss = new ServerSocket(9090);
    //2.
    Socket socket = ss.accept();
    //3.
    InputStream is = socket.getInputStream();
    //4.
    FileOutputStream fos = new FileOutputStream(new File(&quot;beauty1.jpg&quot;));
    //5.
    byte[] buffer = new byte[1024];
    int len;
    while((len = is.read(buffer)) != -1){
        fos.write(buffer,0,len);
    }
    //6.
    fos.close();
    is.close();
    socket.close();
    ss.close();

}
```



}



分析：步骤与例子1是一样的，差别在于服务端保存文件的IO方法。

例子3：从客户端发送文件给服务端，服务端保存到本地。并返回“发送成功”给客户端。并关闭相应的连接。





publicclassTCPTest3 {



```
/*
这里涉及到的异常，应该使用try-catch-finally处理
*/
@Test
public void client() throws IOException {
    //1.
    Socket socket = new Socket(InetAddress.getByName(&quot;127.0.0.1&quot;),9090);
    //2.
    OutputStream os = socket.getOutputStream();
    //3.
    FileInputStream fis = new FileInputStream(new File(&quot;beauty.jpg&quot;));
    //4.
    byte[] buffer = new byte[1024];
    int len;
    while((len = fis.read(buffer)) != -1){
        os.write(buffer,0,len);
    }
    //关闭数据的输出
    socket.shutdownOutput();

    //5.接收来自于服务器端的数据，并显示到控制台上
    InputStream is = socket.getInputStream();
    ByteArrayOutputStream baos = new ByteArrayOutputStream();
    byte[] bufferr = new byte[20];
    int len1;
    while((len1 = is.read(buffer)) != -1){
        baos.write(buffer,0,len1);
    }

    System.out.println(baos.toString());

    //6.
    fis.close();
    os.close();
    socket.close();
    baos.close();
}

/*
这里涉及到的异常，应该使用try-catch-finally处理
 */
@Test
public void server() throws IOException {
    //1.
    ServerSocket ss = new ServerSocket(9090);
    //2.
    Socket socket = ss.accept();
    //3.
    InputStream is = socket.getInputStream();
    //4.
    FileOutputStream fos = new FileOutputStream(new File(&quot;beauty2.jpg&quot;));
    //5.
    byte[] buffer = new byte[1024];
    int len;
    while((len = is.read(buffer)) != -1){
        fos.write(buffer,0,len);
    }

    System.out.println(&quot;图片传输完成&quot;);

    //6.服务器端给予客户端反馈
    OutputStream os = socket.getOutputStream();
    os.write(&quot;你好，美女，照片我已收到，非常漂亮！&quot;.getBytes());

    //7.
    fos.close();
    is.close();
    socket.close();
    ss.close();
    os.close();

}
```



}



## URL网络编程

1.URL:统一资源定位符，对应着互联网的某一资源地址

2.格式：

http://localhost:8080/examples/beauty.jpg?username=Tom

协议　主机名　端口号　　　资源地址　　　　参数列表

- url.getProtocol( )： 获取该URL的协议名
- url.getHost( )： 获取该URL的主机名
- url.getPort( )： 获取该URL的端口号
- url.getPath( )： 获取该URL的文件路径
- url.getFile( )： 获取该URL的文件名
- url.getQuery( )： 获取该URL的查询名

　　　　





publicclass URLTest1 {



```
public static void main(String[] args) {

    HttpURLConnection urlConnection = null;
    InputStream is = null;
    FileOutputStream fos = null;
    try {
        URL url = new URL(&quot;http://localhost:8080/examples/beauty.jpg&quot;);

        urlConnection = (HttpURLConnection) url.openConnection();

        urlConnection.connect();

        is = urlConnection.getInputStream();
        fos = new FileOutputStream(&quot;day10\\beauty3.jpg&quot;);

        byte[] buffer = new byte[1024];
        int len;
        while((len = is.read(buffer)) != -1){
            fos.write(buffer,0,len);
        }

        System.out.println(&quot;下载完成&quot;);
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        //关闭资源
        if(is != null){
            try {
                is.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if(fos != null){
            try {
                fos.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
        if(urlConnection != null){
            urlConnection.disconnect();
        }
    }
}
```



}



## UDP协议的网络编程





publicclass UDPTest {



```
//发送端
@Test
public void sender() throws IOException {

    DatagramSocket socket = new DatagramSocket();



    String str = &quot;我是UDP方式发送的导弹&quot;;
    byte[] data = str.getBytes();
    InetAddress inet = InetAddress.getLocalHost();
    DatagramPacket packet = new DatagramPacket(data,0,data.length,inet,9090);

    socket.send(packet);

    socket.close();

}
//接收端
@Test
public void receiver() throws IOException {

    DatagramSocket socket = new DatagramSocket(9090);

    byte[] buffer = new byte[100];
    DatagramPacket packet = new DatagramPacket(buffer,0,buffer.length);

    socket.receive(packet);

    System.out.println(new String(packet.getData(),0,packet.getLength()));

    socket.close();
}
```



}



# day29

## 反射初步了解

在Person类外部，不可以通过Person类的对象调用其内部私有结构。可以通过反射，创建Person类的对象，调用对象指定的属性、方法，甚至可以通过反射，可以调用Person类的私有结构的。比如：私有的构造器、方法、属性。

疑问1：通过直接new的方式或反射的方式都可以调用公共的结构，开发中到底用那个？

建议：直接new的方式。
什么时候会使用：反射的方式。 反射的特征：动态性

疑问2：反射机制与面向对象中的封装性是不是矛盾的？如何看待两个技术？

不矛盾。

## 关于java.lang.Class类的理解

1. 类的加载过程：
    程序经过javac.exe命令以后，会生成一个或多个字节码文件(.class结尾)。接着我们使用java.exe命令对某个字节码文件进行解释运行。相当于将某个字节码文件加载到内存中。此过程就称为类的加载。加载到内存中的类，我们就称为运行时类，此运行时类，就作为Class的一个实例。
2. 换句话说，Class的实例就对应着一个运行时类。
3. 加载到内存中的运行时类，会缓存一定的时间。在此时间之内，我们可以通过不同的方式 来获取此运行时类。

## 获取Class的实例的方式

（前三种方式需要掌握）

- 方式一：调用运行时类的属性：.class
- 方式二：通过运行时类的对象,调用getClass()
- 方式三：调用Class的静态方法：forName(String classPath) (常用)
- 方式四：使用类的加载器：ClassLoader (了解)

　　　　





public void test3() throws ClassNotFoundException {



//方式一：调用运行时类的属性：.class



​    Class clazz1 = Person.class;



​    System.out.println(clazz1);



//方式二：通过运行时类的对象,调用getClass()



​    Person p1 = new Person();



​    Class clazz2 = p1.getClass();



​    System.out.println(clazz2);



```
//方式三：调用Class的静态方法：forName(String classPath)
Class clazz3 = Class.forName(&quot;com.atguigu.java.Person&quot;);
//clazz3 = Class.forName(&quot;java.lang.String&quot;);
System.out.println(clazz3);

System.out.println(clazz1 == clazz2);
System.out.println(clazz1 == clazz3);

//方式四：使用类的加载器：ClassLoader  (了解)
ClassLoader classLoader = ReflectionTest.class.getClassLoader();
Class clazz4 = classLoader.loadClass(&quot;com.atguigu.java.Person&quot;);
System.out.println(clazz4);

System.out.println(clazz1 == clazz4);
```



}



## Class实例可以是哪些结构

万事万物皆对象





@Test



public void test4(){



​    Class c1 = Object.class;



​    Class c2 = Comparable.class;



​    Class c3 = String[].class;



​    Class c4 = int[][].class;



​    Class c5 = ElementType.class;



​    Class c6 = Override.class;



​    Class c7 = int.class;



​    Class c8 = void.class;



​    Class c9 = Class.class;



```
int[] a = new int[10];
int[] b = new int[100];
Class c10 = a.getClass();
Class c11 = b.getClass();
// 只要数组的元素类型与维度一样，就是同一个Class
System.out.println(c10 == c11);
```



}



## newInstance

newInstance():调用此方法，创建对应的运行时类的对象。内部调用了运行时类的空参的构造器。

要想此方法正常的创建运行时类的对象，要求：
1.运行时类必须提供空参的构造器
2.空参的构造器的访问权限得够。通常，设置为public。

在javabean中要求提供一个public的空参构造器。原因：
1.便于通过反射，创建运行时类的对象
2.便于子类继承此运行时类时，默认调用super()时，保证父类有此构造器

## 了解类的加载器

- 对于自定义类，使用系统类加载器进行加载
- 调用系统类加载器的getParent()：获取扩展类加载器
- 调用扩展类加载器的getParent()：无法获取引导类加载器
- 引导类加载器主要负责加载java的核心类库，无法加载自定义类的。

类加载器作用是用来把类(class)装载进内存的。JVM规范定义了如下类型的类的加载器。

[![img](https://gitee.com/gu097/note/raw/master/img/202110251921030.jpg)](https://images.cnblogs.com/cnblogs_com/kylinxxx/1675669/o_2008040834041596529971(1).jpg)





@Test



public void test1(){



//对于自定义类，使用系统类加载器进行加载



​    ClassLoader classLoader = ClassLoaderTest.class.getClassLoader();



​    System.out.println(classLoader);



//调用系统类加载器的getParent()：获取扩展类加载器



​    ClassLoader classLoader1 = classLoader.getParent();



​    System.out.println(classLoader1);



//调用扩展类加载器的getParent()：无法获取引导类加载器



//引导类加载器主要负责加载java的核心类库，无法加载自定义类的。



​    ClassLoader classLoader2 = classLoader1.getParent();



​    System.out.println(classLoader2);



```
ClassLoader classLoader3 = String.class.getClassLoader();
System.out.println(classLoader3);
```



}



## Properties

Properties:用来读取配置文件





@Test



public void test2() throws Exception {



```
Properties pros =  new Properties();
//此时的文件默认在当前的module下。
//读取配置文件的方式一：
//FileInputStream fis = new FileInputStream(&quot;jdbc.properties&quot;);
//FileInputStream fis = new FileInputStream(&quot;src\\jdbc1.properties&quot;);
//pros.load(fis);

//读取配置文件的方式二：使用ClassLoader
//配置文件默认识别为：当前module的src下
ClassLoader classLoader = ClassLoaderTest.class.getClassLoader();
InputStream is = classLoader.getResourceAsStream(&quot;jdbc1.properties&quot;);
pros.load(is);


String user = pros.getProperty(&quot;user&quot;);
String password = pros.getProperty(&quot;password&quot;);
System.out.println(&quot;user = &quot; + user + &quot;,password = &quot; + password);
```



}



总结：

1. 注意两种方式读取文件的路径不同，方式一在当前module下，方式二在当前module的src下
2. 使用getResourceAsStream读取文件
3. 将要读去的数据写入一个.properties文件中，创建方式New --> Resource Bundle

## 获取运行时类的属性、方法、父类等

- 获取属性结构
    `getFields():获取当前运行时类及其父类中声明为public访问权限的属性`
    `getDeclaredFields():获取当前运行时类中声明的所有属性。（不包含父类中声明的属性）`
- 获取权限修饰符 数据类型 变量名
    `getModifiers():权限修饰符`
    `getType():数据类型`
    `getName():变量名`
- 获取方法结构
    `getMethods():获取当前运行时类及其所有父类中声明为public权限的方法`
    `getDeclaredMethods():获取当前运行时类中声明的所有方法。（不包含父类中声明的方法）`
- 获取注解、权限修饰符、返回值类型、方法名、形参列表、抛出的异常

例如：



```
`/*
@Xxxx
权限修饰符  返回值类型  方法名(参数类型1 形参名1,...) throws XxxException{}
 */`
getAnnotations(): 获取方法声明的注解`
`Modifier.toString(m.getModifiers()): 权限修饰符`
获取的权限修饰符比较特殊， getModifiers()返回的是int类型（如1， 2， 3， 4），这些数字分别代表public， protected等
使用Modifier.toString将它转化为字符串形式的权限修饰符 `getReturnType().getName():返回值类型`
`getName()
```

形参列表



```java
 Class[] parameterTypes = m.getParameterTypes();
    if(!(parameterTypes == null && parameterTypes.length == 0)){
        for(int i = 0;i < parameterTypes.length;i++){
        if(i == parameterTypes.length - 1){
            System.out.print(parameterTypes[i].getName() + &quot; args_&quot; + i);
            break;
        }

        System.out.print(parameterTypes[i].getName() + &quot; args_&quot; + i + &quot;,&quot;);
    }
}
```

抛出的异常

```java
Class[] parameterTypes = m.getParameterTypes();
    if(!(parameterTypes == null && parameterTypes.length == 0)){
        for(int i = 0;i < parameterTypes.length;i++){
        if(i == parameterTypes.length - 1){
            System.out.print(parameterTypes[i].getName() + &quot; args_&quot; + i);
            break;
        }

        System.out.print(parameterTypes[i].getName() + &quot; args_&quot; + i + &quot;,&quot;);
    }
}
```