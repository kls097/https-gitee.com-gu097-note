# JDK和JRE有什么区别？

- JRE：java 运行时环境，包含了java虚拟机、java基础类库
- JDK：java 开发工具包，包含了JRE，同时还包含了java编译器javac、监控工具jconsole、分析工具jvisualvm

# ==和equals的区别是什么?

- == 是关系运算符，equals() 是方法，结果都返回布尔值
- Object 的 == 和 equals() 比较的都是地址，作用相同

细说：
\- `==`：基本类型，比较值是否相等；引用类型，比较内存地址值是否相等 - `equals()`：JDK 中的类一般已经重写了 equals()，比较的是内容，如果自定义类如果没有重写 equals()，将调用父类（默认 Object 类）的 equals() 方法，Object 的 equals() 比较使用了 this == obj，可以重写equals（）方法。

# 基本类型和包装类对象使用 == 和 equals进行比较的结果？

- 值不同，使用 ＝＝ 和 equals() 比较都返回 false
- 值相同
    - 使用==比较
        - 基本类型 与 基本类型、基本类型 与 包装对象返回 true
        - 包装对象 与 包装对象，非同一个对象（对象的内存地址不同）返回 false；对象的内存地址相同返回 true
    - 使用equlas()比较
        - 包装对象 与 基本类型返回 true
        - 包装对象 与 包装对象返回 true

# 什么是装箱？什么是拆箱？装箱和拆箱的执行过程？常见问题？

> 什么是装箱

- 装箱：基本类型转变为包装器类型的过程。
- 拆箱：包装器类型转变为基本类型的过程。
- JDK1.5开始，提供了自动装箱/自动拆箱的功能

> 装箱和拆箱的执行过程？

- 装箱是通过调用包装器类的 valueOf 方法实现的
- 拆箱是通过调用包装器类的 xxxValue 方法实现的，xxx代表对应的基本数据类型。

> 常见问题？

- 整型的包装类 valueOf 方法返回对象时，在常用的取值范围内，会返回缓存对象。(-128-127)
- 浮点型的包装类 valueOf 方法返回新的对象。
- 布尔型的包装类 valueOf 方法 Boolean类的静态常量 TRUE | FALSE。

# hashCode()相同，equals()也一定为true吗？

答案肯定是不一定。同时反过来 equals() 为true，hashCode() 也不一定相同。

(1)两个对象相等，hashcode一定相等
(2)两个对象不等，hashcode不一定不等
(3)hashcode相等，两个对象不一定相等
(4)hashcode不等，两个对象一定不等

# final在java中的作用

final 语义是不可改变的。

- 被 final 修饰的类，不能够被继承
- 被 final 修饰的成员变量必须要初始化，赋初值后不能再重新赋值(可以调用对象方法修改属性值)。对基本类型来说是其值不可变；对引用变量来说其引用不可变，即不能再指向其他的对象
- 被 final 修饰的方法不能重写，但能重载

# final finally finalize()区别

> final 语义是不可改变的。

- 被 final 修饰的类，不能够被继承
- 被 final 修饰的成员变量必须要初始化，赋初值后不能再重新赋值(可以调用对象方法修改属性值)。对基本类型来说是其值不可变；对引用变量来说其引用不可变，即不能再指向其他的对象
- 被 final 修饰的方法不能重写，但能重载

> finally 用于异常处理

它只能用在 try/catch 语句中，表示希望 finally 语句块中的代码最后一定被执行

> finalize()是个方法

finalize()方法在Object中进行了定义，用于在对象“消失”时，由JVM进行调用用于对对象进行垃圾回收

# finally语句块一定执行吗？

不一定

- 直接返回未执行到finally语句块（try中有return）
- 抛出异常未执行到finally语句块（try语句之前就已经有异常）
- 系统退出未执行到finally语句块（System.exit()方法）

演示如下：

```
public static String test() {
    String str = null;
    int i = 0;
    if (i == 0) {
        return str;//直接返回未执行到finally语句块
    }
    try {
        System.out.println("try...");
        return str;
    } finally {
        System.out.println("finally...");
    }
}
public static String test2() {
String str = null;
int i = 0;
i = i / 0;//抛出异常未执行到finally语句块
try {
System.out.println("try...");
return str;
} finally {
System.out.println("finally...");
}
}
public static String test3() {
String str = null;
try {
System.out.println("try...");
System.exit(0);//系统退出未执行到finally语句块
return str;
} finally {
System.out.println("finally...");
}
}
```



# final与static的区别

- static
    - static 修饰表示静态或全局，被修饰的属性和方法属于类，可以用类名.静态属性 / 方法名 访问
    - static 修饰的代码块表示静态代码块，当 Java 虚拟机（JVM）加载类时，就会执行该代码块,只会被执行一次
    - static 修饰的属性，也就是类变量，是在类加载时被创建并进行初始化，只会被创建一次
    - static 修饰的变量可以重新赋值
    - static 方法中不能用 this 和 super 关键字
    - static 方法必须被实现，而不能是抽象的abstract
    - static 方法不能被重写
- final
    - final 修饰表示常量、一旦创建不可改变
    - final 标记的成员变量必须在声明的同时赋值，或在该类的构造方法中赋值，不可以重新赋值
    - final 方法不能被子类重写
    - final 类不能被继承，没有子类，final 类中的方法默认是 final 的
- 总而言之
    - 都可以修饰类、方法、成员变量。
    - 都不能用于修饰构造方法。
    - static 可以修饰类的代码块，final 不可以。
    - static 不可以修饰方法内的局部变量，final 可以。

# String对象中的replace和replaceAll的区别？

- 参数不同
    - replace方法：支持字符和字符串的替换。
    - replaceAll方法：基于正则表达式的字符串替换。
- 替换不同
    - replace只替换第一个出现的字符
    - replaceall替换所有的字符

# Math.round(-1.5) 等于多少？

-1

- ceil() ：向上取整，返回小数所在两整数间的较大值，返回类型是 double，如 -1.5 返回 -1.0
- floor() ：向下取整，返回小数所在两整数间的较小值，返回类型是 double，如 -1.5 返回 -2.0
- round() ：朝正无穷大方向返回参数最接近的整数，可以换算为 参数 + 0.5 向下取整，返回值是 int 或 long，如 -1.5 返回 -1

# String属于基础的数据类型吗？

不属于。

Java 中 8 种基础的数据类型：byte、short、char、int、long、float、double、boolean

但是 String 类型却是最常用到的引用类型。

# java中操作字符串都有哪些类？它们之间有什么区别？（或问String、StringBuffer、StringBuilder的区别）

- String : final 修饰，String 类的方法都是返回 new String。即对 String 对象的任何改变都不影响到原对象，对字符串的修改操作都会生成新的对象。
- StringBuffer : 对字符串的操作的方法都加了synchronized，保证线程安全。
- StringBuilder : 不保证线程安全，在方法体内需要进行字符串的修改操作，可以 new StringBuilder 对象，调用 StringBuilder 对象的 append()、replace()、delete() 等方法修改字符串。
- StringBuilder速度最快，StringBuffer次之，String最慢

# String、StringBuilder、StringBuffer的区别?

相同点：

- 都可以储存和操作字符串
- 都使用 final 修饰，不能被继承
- 提供的 API 相似

区别：

- String 是只读字符串，String 对象内容是不能被改变的
- StringBuffer 和 StringBuilder 的字符串对象可以对字符串内容进行修改，在修改后的内存地址不会发生改变
- StringBuilder 线程不安全；StringBuffer 线程安全

# 如何将字符串反转？

- 使用 StringBuilder 或 StringBuffer 的 reverse 方法
- 自己实现的话可以利用栈或递归

# String类的常用方法有哪些（几乎不会问，但是方法很多没事看一看）



```
equals：字符串是否相同
equalsIgnoreCase：忽略大小写后字符串是否相同
compareTo：根据字符串中每个字符的Unicode编码进行比较
compareToIgnoreCase：根据字符串中每个字符的Unicode编码进行忽略大小写比较
indexOf：目标字符或字符串在源字符串中位置下标
lastIndexOf：目标字符或字符串在源字符串中最后一次出现的位置下标
valueOf：其他类型转字符串
charAt：获取指定下标位置的字符
codePointAt：指定下标的字符的Unicode编码
concat：追加字符串到当前字符串
isEmpty：字符串长度是否为0
contains：是否包含目标字符串
startsWith：是否以目标字符串开头
endsWith：是否以目标字符串结束
format：格式化字符串
getBytes：获取字符串的字节数组
getChars：获取字符串的指定长度字符数组
toCharArray：获取字符串的字符数组
join：以某字符串，连接某字符串数组
length：字符串字符数
matches：字符串是否匹配正则表达式
replace：字符串替换
replaceAll：带正则字符串替换
replaceFirst：替换第一个出现的目标字符串
split：以某正则表达式分割字符串
substring：截取字符串
toLowerCase：字符串转小写
toUpperCase：字符串转大写
trim：去字符串首尾空格
```

# 普通类和抽象类有哪些区别？

- 抽象类不能被实例化
- 抽象类可以有抽象方法，抽象方法只需申明，无需实现
- 含有抽象方法的类必须申明为抽象类
- 抽象类的子类必须实现抽象类中所有抽象方法，否则这个子类也是抽象类
- 抽象方法不能被声明为静态
- 抽象方法不能用 private 修饰
- 抽象方法不能用 final 修饰

## 扩展——抽象类必须要有抽象方法吗？

不一定，如





publicabstractclassTestAbstractClass {



```
public static void notAbstractMethod() {
    System.out.println(&quot;I am not a abstract method.&quot;);
}
```



}



# 接口和抽象类有什么区别

- 抽象类可以有构造方法；接口中不能有构造方法。
- 抽象类中可以有普通成员变量；接口中没有普通成员变量。
- 抽象类中的抽象方法的访问权限可以是 public、protected 和 default；接口中的抽象方法只能是 public 类型的
- 抽象类和接口中都可以包含静态成员变量，抽象类中的静态成员变量可以是任意访问权限；接口中变量默认且只能是 public static final 类型。
- 一个类可以实现多个接口，用逗号隔开，但只能继承一个抽象类。
- 接口不可以实现接口，但可以继承接口，并且可以继承多个接口，用逗号隔开。

# Java访问修饰符有哪些？权限的区别？

Java中有四种权限修饰符：



```
                    public  >   protected   >   (default)   >   private
同一个类（我自己）        YES         YES             YES             YES
同一个包（我邻居）        YES         YES             YES             NO
不同包子类（我儿子）      YES         YES              NO              NO
不同包非子类（陌生人）      ES         NO              NO              NO
```

# javap的作用是什么

javap 是 Java class文件分解器，可以反编译，也可以查看 java 编译器生成的字节码等。

# throw和throws的区别？

- throw：
    - 表示方法内抛出某种异常对象(只能是一个)
    - 用于程序员自行产生并抛出异常
    - 位于方法体内部，可以作为单独语句使用
    - 执行到 throw 语句则后面的语句块不再执行
- throws：
    - 方法的定义上使用 throws 表示这个方法可能抛出某些异常(可以有多个)
    - 用于声明在该方法内抛出了异常
    - 必须跟在方法参数列表的后面，不能单独使用
    - 需要由方法的调用者进行异常处理

# 常见的异常类有哪些？

- CloneNotSupportedException
- DataFormatException
- IOException
- InterruptedException
- SQLException
- RuntimeException

# 什么是反射？有什么作用？

Java 反射，就是在运行状态中

- 获取任意类的名称、package 信息、所有属性、方法、注解、类型、类加载器、modifiers（public、static）、父类、现实接口等
- 获取任意对象的属性，并且能改变对象的属性
- 调用任意对象的方法
- 判断任意一个对象所属的类
- 实例化任意一个类的对象
- Java 的动态就体现在反射。通过反射我们可以实现动态装配，降低代码的耦合度；动态代理等。反射的过度使用会严重消耗系统资源。

JDK 中 java.lang.Class 类，就是为了实现反射提供的核心类之一。

一个 jvm 中一种 Class 只会被加载一次。

# 动态代理是什么？应用场景？

动态代理：在运行时，创建目标类，可以调用和扩展目标类的方法。

Java 中实现动态的方式：

- JDK 中的动态代理
- Java类库 CGLib
- 使用 Spring aop 模块完成动态代理功能

应用场景：



```
统计每个 api 的请求耗时
统一的日志输出
校验被调用的 api 是否已经登录和权限鉴定
Spring的 AOP 功能模块就是采用动态代理的机制来实现切面编程
```

# Java跨平台运行的原理

1、.java 源文件要先编译成与操作系统无关的 .class 字节码文件，然后字节码文件再通过 Java 虚拟机解释成机器码运行。

2、.class 字节码文件面向虚拟机，不面向任何具体操作系统。

3、不同平台的虚拟机是不同的，但它们给 JDK 提供了相同的接口。

4、Java 的跨平台依赖于不同系统的 Java 虚拟机。

# JDK、JRE、JVM之间的关系是什么样的？

- JDK 是 JAVA 程序开发时用的开发工具包，包含 Java 运行环境 JRE
- JDk、JRE 内部都包含 JAVA虚拟机 JVM
- JVM 包含 Java 应用程序的类的解释器和类加载器等

# Java中有几种基本数据类型？它们分别占多大字节？



```
byte：1个字节，8位
short：2个字节，16位
int：4个字节，32位
long：8个字节，64位
float：4个字节，32位
double：8个字节，64位
boolean：官方文档未明确定义，依赖于 JVM 厂商的具体实现。逻辑上理解是占用 1位，但是实际中会考虑计算机高效存储因素
char：2个字节，16位
```

# i++和++i的作用和区别

作用：都是给变量 i 加 1，相当于 i = i + 1;

区别：

- i++ 先运算后加 1
- ++i 先加 1 再运算

# 如何让计算机最高效的算出2乘以8？

2 <<3

# 什么是Java的多态？

> 实现多态的三个条件

- 继承的存在。继承是多态的基础，没有继承就没有多态
- 子类重写父类的方法，JVM 会调用子类重写后的方法
- 父类引用变量指向子类对象

> 向上转型：将一个父类的引用指向一个子类对象，自动进行类型转换。

- 通过父类引用变量调用的方法是子类覆盖或继承父类的方法，而不是父类的方法。
- 通过父类引用变量无法调用子类特有的方法。

> 向下转型：将一个指向子类对象的引用赋给一个子类的引用，必须进行强制类型转换。

- 向下转型必须转换为父类引用指向的真实子类类型，不是任意的强制转换，否则会出现 ClassCastException
- 向下转型时可以结合使用 instanceof 运算符进行判断

# instanceof关键字的作用是什么？

instanceof 运算符是用来在运行时判断对象是否是指定类及其父类的一个实例。

比较的是对象，不能比较基本类型

# java.sql.Date和java.util.Date的区别

- java.sql.Date 是 java.util.Date 的子类
- java.util.Date 是 JDK 中的日期类，精确到时、分、秒、毫秒
- java.sql.Date 与数据库 Date 相对应的一个类型，只有日期部分，时分秒都会设置为 0，如：2019-10-23 00:00:00
- 要从数据库时间字段取 时、分、秒、毫秒数据，可以使用 java.sql.Timestamp

# 构造方法在一个对象被 new 时执行

# 一个类中可以定义多个构造方法，这就是构造方法的重载

# 说说你对面向对象的理解

对 Java 语言来说，一切皆是对象。

对象有以下特点：

- 对象具有属性和行为
- 对象具有变化的状态
- 对象具有唯一性
- 对象都是某个类别的实例
- 一切皆为对象，真实世界中的所有事物都可以视为对象

面向对象的特性：

- 抽象性：抽象是将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象两方面。
- 继承性：指子类拥有父类的全部特征和行为，这是类之间的一种关系。Java 只支持单继承。
- 封装性：封装是将代码及其处理的数据绑定在一起的一种编程机制，该机制保证了程序和数据都不受外部干扰且不被误用。封装的目的在于保护信息。
- 多态性：多态性体现在父类的属性和方法被子类继承后或接口被实现类实现后，可以具有不同的属性或表现方式。

# 内存泄漏和内存溢出的区别

- 内存溢出(out of memory)：指程序在申请内存时，没有足够的内存空间供其使用，出现 out of memory。
- 内存泄露(memory leak)：指程序在申请内存后，无法释放已申请的内存空间，内存泄露堆积会导致内存被占光。

# 同步代码块和同步方法有什么区别？

- 同步方法就是在方法前加关键字 synchronized；同步代码块则是在方法内部使用 synchronized
- 加锁对象相同的话，同步方法锁的范围大于等于同步方法块。一般加锁范围越大，性能越差
- 同步方法如果是 static 方法，等同于同步方法块加锁在该 Class 对象上

# 静态内部类和非静态内部类有什么区别？

- 静态内部类不需要有指向外部类的引用；非静态内部类需要持有对外部类的引用
- 静态内部类可以有静态方法、属性；非静态内部类则不能有静态方法、属性
- 静态内部类只能访问外部类的静态成员，不能访问外部类的非静态成员；非静态内部类能够访问外部类的静态和非静态成员
- 静态内部类不依赖于外部类的实例，直接实例化内部类对象；非静态内部类通过外部类的对象实例生成内部类对象

# 构造方法是否可以被重载？重写？

构造方法可以被重载

构造方法不可以被重写

# 日期类型如何格式化？字符串如何转日期？

日期格式为字符串



```
DateFormat  sdf = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
String s = sdf.format(new Date());
```

字符串转日期



```
DateFormat  sdf = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");
String s = "2019-10-31 22:53:10";
Date date = sdf.parse(s);
```

# abstract方法是否可是static的？native的？synchronized的?

- 抽象方法需要子类重写，而静态的方法是无法被重写的
- 本地方法是由本地动态库实现的方法，而抽象方法是没有实现的
- 抽象方法没有方法体；synchronized 方法，需要有具体的方法体，相互矛盾

# 静态方法与实例方法的区别

1、静态方法属于整个类所有，因此调用它不需要实例化，可以直接调用（类.静态方法（））。实例方法必须先实例化，创建一个对象，才能进行调用（对象.实例方法（））。 2、静态方法只能访问静态成员，不能访问实例成员；而实例方法可以访问静态成员和实例成员。 3、在程序运行期间，静态方法是一直存放在内存中，因此调用速度快，但是却占用内存。实例方法是使用完成后由回收机制自动进行回收，下次再使用必须再实例化。 4、一般来说，公共的函数、经常调用的可以写成静态方法，比如数据连接等（SqlHelper)。

# 基本类型和包装类型的区别

Java 的每个基本类型都对应了一个包装类型，比如说 int 的包装类型为 Integer，double 的包装类型为 Double。

- 包装类型可以为 null，而基本类型不可以
- 包装类型可用于泛型，而基本类型不可以
- 基本类型比包装类型更高效
- 自动装箱和自动拆箱

# 说说反射在你实际开发中的使用

反射使用不好，对性能影响比较，一般项目中很少直接使用。

反射主要用于底层的框架中，Spring 中就大量使用了反射，比如：

- 用 IoC 来注入和组装 bean
- 动态代理、面向切面、bean 对象中的方法替换与增强，也使用了反射
- 定义的注解，也是通过反射查找