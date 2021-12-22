# 1、类

## 1、封装性

类的封装性即不能让外面的类随意修改一个类的成员变量；

在定义一个类的成员，使用private关键字说明这个成员的访问权限，只能被这个类的其他成员方法调用，而不能被其他的类中的方法所调用；

为实现封装性，常将类的成员变量声明为private,再通过public的方法来对这个变量进行访问。对一个变量的操作，一般都有 读取和赋值操作，我们一般定义两个方法来实现这两种操作，即：getxxx()与setxxx();

一个类就是一个模块，我们应该让模块仅仅公开必须要让外界知道的内容，而隐藏其他的一切内容。再进行程序设计时，应尽量避免一个模块直接修改或操作另一个模块的数据。

总结一下就是类按需求使用方法暴漏对类内部变量的set与get方法以及一些其它所需方法，而类内部的结构则对外隐藏。



封装性的体现：① 如上 ② 不对外暴露的私有的方法 ③ 单例模式 ...

三、封装性的体现，需要权限修饰符来配合。

1.Java规定的4种权限（从小到大排列）：private、缺省、protected 、public

2.4种权限可以用来修饰类及类的内部结构：属性、方法、构造器、内部类

3.具体的，4种权限都可以用来修饰类的内部结构：属性、方法、构造器、内部类

> 修饰类的话，只能使用：缺省、public

- 总结封装性：Java提供了4种权限修饰符来修饰类及类的内部结构，体现类及类的内部结构在被调用时的可见性的大小。



## 2、四种访问权限修饰符

Java权限修饰符public、protected、private置于*类的成员*定义前，用来限定对象对该类成员的访问权限

| 修饰符    | 类内部 | 同一个包 | 不同包的子类 | 同一个工程 |
| :-------- | :----- | :------- | :----------- | :--------- |
| private   | Yes    |          |              |            |
| （缺省）  | Yes    | Yes      |              |            |
| protected | Yes    | Yes      | Yes          |            |
| public    | Yes    | Yes      | Yes          | Yes        |

简单总结，

private：只能在当前类内部

缺省：当前包内部

protected：不仅包括当前包的所有类可以访问，以及它的所有子类都可以访问，不管是不是与它在用一个包下

public：当前工程均可访问



对于class的权限修饰只可以用public和default（缺省）

> public类可以在任意地方被访问
>
> default类只可以被同一个包内部的类访问





## 3、构造器

**一、构造器的作用：**

​	1.创建对象

​	2.初始化对象的信息

**二、说明：**

1.**如果没有显式的定义类的构造器的话，则系统默认提供一个空参的构造器**

2.定义构造器的格式：权限修饰符 类名(形参列表){}

3.**一个类中定义的多个构造器，彼此构成重载**

4.**一旦我们显式的定义了类的构造器之后，系统就不再提供默认的空参构造器**

5.**一个类中，至少会有一个构造器。**

总结：属性赋值的先后顺序

① 默认初始化

② 显式初始化

③ 构造器中初始化

④ 通过"对象.方法" 或 "对象.属性"的方式，赋值

以上操作的先后顺序：① - ② - ③ - ④



## 4、JavaBean

就是平时用的pojo模版类。

JavaBean是一种Java语言写成的可重用组件。

所谓JavaBean，是指符合如下标准的Java类：

> 类是公共的
>
> 有一个无参的公共的构造器
>
> 有属性，且有对应的get、set方法



## 5、this

① 我们在类的构造器中，可以显式的使用"this(形参列表)"方式，调用本类中指定的其他构造器

② **构造器中不能通过"this(形参列表)"方式调用自己**

③ 如果一个类中有n个构造器，则最多有 n - 1构造器中使用了"this(形参列表)"

④ **规定："this(形参列表)"必须声明在当前构造器的首行**

⑤ **构造器内部，最多只能声明一个"this(形参列表)"，用来调用其他的构造器**



## 6、package和import

**一、package关键字的使用**

1.为了更好的实现项目中类的管理，提供包的概念

2.使用package声明类或接口所属的包，声明在源文件的首行

3.包，属于标识符，遵循标识符的命名规则、规范(xxxyyyzzz)、“见名知意”

4.**每"."一次，就代表一层文件目录。**

补充：**同一个包下，不能命名同名的接口、类。不同的包下，可以命名同名的接口、类。**

**二、import关键字的使用**

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



## 7、Java中的JUnit单元测试

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



## 8、JDK中主要的包介绍（重要）

java.lang ------ 包含一些Java语言的核心类，如String、Math、Integer、System、Thread，提供常用功能

java.net ------ 包含执行与网络相关的操作的类和接口

java.io ------ 包含能够提供多种输入/输出功能的类

java.util ------ 包含一些实用工具类，如定义系统特性、接口的集合框架类、使用与日期日历相关的函数

java.text ------ 包含了一些java格式化相关的类

java.sql ------ 包含了java进行JDBC数据库编程的相关类/接口

java.awt ------ 包含了构成抽象窗口工具集（abstract window toolkits)的多个类，这些类被用来构建和管理应用程序的图形用户界面（GUI）



## 9、继承性

一、继承性的好处：

**① 减少了代码的冗余，提高了代码的复用性**

② 便于功能的扩展

③ 为之后多态性的使用，提供了前提

二、继承性的格式： `class A extends B{}`

**A:子类、派生类、subclass**

B:父类、超类、基类、superclass

2.1体现：一旦子类A继承父类B以后，子类A中就获取了父类B中声明的所有的属性和方法。**特别的，父类中声明为private的属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构。只有因为封装性的影响，使得子类不能直接调用父类的结构而已。**

2.2 子类继承父类以后，还可以声明自己特有的属性或方法：实现功能的拓展。子类和父类的关系，不同于子集和集合的关系。

**extends：延展、扩展**

三、Java中关于继承性的规定：

1.一个类可以被多个子类继承。

**2.Java中类的单继承性：一个类只能有一个父类**

3.子父类是相对的概念。

4.子类直接继承的父类，称为：直接父类。间接继承的父类称为：**间接父类**

5.子类继承父类以后，**就获取了直接父类以及所有间接父类中声明的属性和方法**

四、 1.如果我们没有显式的声明一个类的父类的话，则此类继承于java.lang.Object类

2.所有的java类（除java.lang.Object类之外）都直接或间接的继承于java.lang.Object类

3.意味着，**所有的java类具有java.lang.Object类声明的功能。**



## 10、方法的重写(override / overwrite)

1.重写：子类继承父类以后，可以对父类中同名同参数的方法，进行覆盖操作

2.应用：重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，实**际执行的是子类重写父类的方法。**

1. 重写的规定：

    方法的声明： 权限修饰符 返回值类型 方法名(形参列表) throws 异常的类型{}

约定俗称：子类中的叫重写的方法，父类中的叫被重写的方法

① 子类重写的方法的方法名和形参列表与父类被重写的方法的方法名和形参列表相同

② 子类重写的方法的权限修饰符不小于父类被重写的方法的权限修饰符

③ 返回值类型：**重写的方法返回值必须相同**

> 父类被重写的方法的返回值类型是void，则子类重写的方法的返回值类型只能是void
>
> 父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A类的子类
>
> 父类被重写的方法的返回值类型是基本数据类型(比如：double)，则子类重写的方法的返回值类型必须是相同的基本数据类型(必须也是double)

④ **子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型**（具体放到异常处理时候讲）

子类和父类中的同名同参数的方法要么都声明为非static的（考虑重写），要么都声明为static的（不是重写）。

- 面试题：区分方法的重载与重写



## 11、super关键字的使用

使用场景：父类方法被重写、子类中定义了与父类同名的属性时，使用super调用父类的属性与方法

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



## 12、子类对象实例化的全过程

1.从结果上来看：（继承性）

- 子类继承父类以后，就获取了父类中声明的属性或方法。
- **创建子类的对象，在堆空间中，就会加载所有父类中声明的属性。**

2.从过程上来看：

- **当我们通过子类的构造器创建子类对象时，我们一定会直接或间接的调用其父类的构造器，进而调用父类的父类的构造器，...**直到调用了java.lang.Object类中空参的构造器为止。正因为加载过所有的父类的结构，所以才可以看到内存中有父类中的结构，子类对象才可以考虑进行调用。

**明确**：虽然创建子类对象时，调用了父类的构造器，但是**自始至终就创建过一个对象**，即为new的子类对象



## 13、多态性

1.理解多态性：可以理解为一个事物的多种形态。

2.何为多态性：

对象的多态性：**父类的引用指向子类的对象（或子类的对象赋给父类的引用）**

**Parent p = new Child();**

1. 多态的使用：虚拟方法调用

有了对象的多态性以后，我们在编译期，**只能调用父类中声明的方法，但在运行期，我们实际执行的是子类重写父类的方法。**

总结：编译，看左边；运行，看右边。

4.多态性的使用前提： ① 类的继承关系 ② 方法的重写

5.对象的多态性，只适用于方法，不适用于属性（编译和运行都看左边）



**相当于一个披着父类外壳的子类，内部都是子类的的，但是外显的所有方法、属性都是父类的。**





## 14、java.lang.Object类

1.Object类是所有Java类的根父类

2.如果在类的声明中未使用extends关键字指明其父类，则默认父类为java.lang.Object类

3.Object类中的功能(属性、方法)就具有通用性。

- 属性：无
- 方法：equals() / toString() / getClass() /hashCode() / clone() / finalize() / wait() 、 notify()、notifyAll()

4.Object类只声明了一个空参的构造器



## 15、equals()

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



## 16、Object类中toString()的使用：

1.当我们输出一个对象的引用时，实际上就是调用当前对象的toString()

2.Object类中toString()的定义：

```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
 }
```

3.像String、Date、File、包装类等都重写了Object类中的toString()方法。使得在调用对象的toString()时，返回"实体内容"信息

4.自定义类也可以重写toString()方法，当调用此方法时，返回对象的"实体内容"

## 17、包装类

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



![img](https://gitee.com/gu097/note/raw/master/img/202110251921858.png)

**包装类面试题**

题1

[![img](https://gitee.com/gu097/note/raw/master/img/202110251921655.png)](https://images.cnblogs.com/cnblogs_com/kylinxxx/1675669/t_2006081655491591635314(1).png)

答案：第一题是1.0；第二题是1。 解析：`true ? new Integer(1) : new Double(2.0);`编译的时候，这段代码得保证true后面的数据类型一致，所以提升为Double

题2（重要！！！）

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



## 18、包装类缓存区与比较

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

​	true

​	false





# 2、关键字、方法、内部成员

## 1、static关键字的使用

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

## 2、单例设计模式：

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

## 3、main()方法的使用说明：

- 1. main()方法作为程序的入口
- 2. main()方法也是一个普通的静态方法
- 3. main()方法可以作为我们与控制台交互的方式。（之前：使用Scanner）

## 4、类的成员之四：代码块（或初始化块）

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

## 5、final关键字

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



## 6、abstract关键字的使用

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

## 7、abstract使用上的注意点：

1.abstract不能用来修饰：属性、构造器等结构

2.abstract不能用来修饰私有方法、静态方法、final的方法、final的类

## 8、接口的使用

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

## 9、类的内部成员之五：内部类

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



# 3、错误与异常

![img](https://gitee.com/gu097/note/raw/master/img/202110251922846.jpg)

## 1、Error:

Java虚拟机无法解决的严重问题。如：JVM系统内部错误、资源耗尽等严重情况。比如：StackOverflowError和OOM。

一般不编写针对性的代码进行处理。

## 2、java.lang.Throwable

- java.lang.Error:一般不编写针对性的代码进行处理。
- java.lang.Exception:可以进行异常的处理

## 3、编译时异常(checked)

> IOException
>
> > FileNotFoundException
>
> ClassNotFoundException

## 4、运行时异常(unchecked,RuntimeException)

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



# 4、线程

## 1、Thread中的常用方法：

1. start():启动当前线程；调用当前线程的run()
2. run(): 通常需要重写Thread类中的此方法，将创建的线程要执行的操作声明在此方法中
3. currentThread():静态方法，返回执行当前代码的线程
4. getName():获取当前线程的名字
5. setName():设置当前线程的名字
6. yield():释放当前cpu的执行权
7. join():在线程a中调用线程b的join(),此时线程a就进入阻塞状态，直到线程b完全执行完以后，线程a才结束阻塞状态。
8. stop():已过时。当执行此方法时，强制结束当前线程。
9. sleep(long millitime):让当前线程“睡眠”指定的millitime毫秒。在指定的millitime毫秒时间内，当前线程是阻塞状态。
10. isAlive():判断当前线程是否存活

线程的优先级：

1. 

- MAX_PRIORITY：10
- MIN _PRIORITY：1
- NORM_PRIORITY：5 -->默认优先级

2.如何获取和设置当前线程的优先级：

- getPriority():获取线程的优先级
- setPriority(int p):设置线程的优先级

说明：高优先级的线程要抢占低优先级线程cpu的执行权。但是只是从概率上讲，高优先级的线程高概率的情况下被执行。并不意味着只有当高优先级的线程执行完以后，低优先级的线程才执行。

示例：`h1.setPriority(Thread.MAX_PRIORITY)`

```java
Thread.currentThread().getPriority()
```

## 2、多线程的创建，方式一：继承于Thread类

1. 创建一个继承于Thread类的子类
2. 重写Thread类的run() --> 将此线程执行的操作声明在run()中
3. 创建Thread类的子类的对象
4. 通过此对象调用start()

## 3、创建多线程的方式二：实现Runnable接口

1. 创建一个实现了Runnable接口的类
2. 实现类去实现Runnable中的抽象方法：run()
3. 创建实现类的对象
4. 将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
5. 通过Thread类的对象调用start()

比较创建线程的两种方式。

开发中：优先选择：实现Runnable接口的方式

原因：

- 1.实现的方式没有类的单继承性的局限性
- 2.实现的方式更适合来处理多个线程有共享数据的情况。

联系：public class Thread implements Runnable

相同点：两种方式都需要重写run(),将线程要执行的逻辑声明在run()中。

## 4、关于售票例子的思考

1. 问题：卖票过程中，出现了重票、错票 -->出现了线程的安全问题
2. 问题出现的原因：当某个线程操作车票的过程中，尚未操作完成时，其他线程参与进来，也操作车票。
3. 如何解决：当一个线程a在操作ticket的时候，其他线程不能参与进来。直到线程a操作完ticket时，其他线程才可以开始操作ticket。这种情况即使线程a出现了阻塞，也不能被改变。

## 5、同步机制,解决线程安全问题

4.在Java中，我们通过同步机制，来解决线程的安全问题。

方式一：同步代码块

```java
synchronized(同步监视器){ //需要被同步的代码 }
```

说明：

- 1.操作共享数据的代码，即为需要被同步的代码。 -->不能包含代码多了，也不能包含代码少了。

- 2.共享数据：多个线程共同操作的变量。比如：ticket就是共享数据。

- 3.同步监视器，俗称：锁。任何一个类的对象，都可以充当锁。

- 要求：多个线程必须要共用同一把锁。

- 补充：在实现Runnable接口创建多线程的方式中，我们可以考虑使用this充当同步监视器。

- 说明：在继承Thread类创建多线程的方式中，慎用this充当同步监视器，考虑使用当前类充当同步监视器。

  ​    

方式二：同步方法。

如果操作共享数据的代码完整的声明在一个方法中，我们不妨将此方法声明同步的。

5.同步的方式，解决了线程的安全问题。---好处

操作同步代码时，只能有一个线程参与，其他线程等待。相当于是一个单线程的过程，效率低。 ---局限性

## 关于同步方法的总结：

1. 同步方法仍然涉及到同步监视器，只是不需要我们显式的声明。
2. 非静态的同步方法，同步监视器是：this;
    静态的同步方法，同步监视器是：当前类本身

## 使用同步机制将单例模式中的懒汉式改写为线程安全的

复习：

懒汉式：

```java
public class SingletonTest2 {
	public static void main(String[] args) {
		
		Order order1 = Order.getInstance();
		Order order2 = Order.getInstance();
		
		System.out.println(order1 == order2);
		
	}
}


class Order{
	
	//1.私有化类的构造器
	private Order(){
		
	}
	
	//2.声明当前类对象，没有初始化
	//4.此对象也必须声明为static的
	private static Order instance = null;
	
	//3.声明public、static的返回当前类对象的方法
	public static Order getInstance(){
		
		if(instance == null){
			
			instance = new Order();
			
		}
		return instance;
	}
	
}
```

线程安全的懒汉式：

```java
public class BankTest {

}

class Bank{

    private Bank(){}

    private static Bank instance = null;

    public static Bank getInstance(){
        //方式一：效率稍差
//        synchronized (Bank.class) {
//            if(instance == null){
//
//                instance = new Bank();
//            }
//            return instance;
//        }
        //方式二：效率更高
        if(instance == null){

            synchronized (Bank.class) {
                if(instance == null){

                    instance = new Bank();
                }

            }
        }
        return instance;
    }

}
```

## 死锁

1.死锁的理解：不同的线程分别占用对方需要的同步资源不放弃，都在等待对方放弃自己需要的同步资源，就形成了线程的死锁

2.说明：

1）出现死锁后，不会出现异常，不会出现提示，只是所有的线程都处于阻塞状态，无法继续

2）我们使用同步时，要避免出现死锁。

## 解决线程安全问题的方式三：Lock锁 --- JDK5.0新增

1. synchronized 与 Lock的异同？

- 相同：二者都可以解决线程安全问题
- 不同：synchronized机制在执行完相应的同步代码以后，自动的释放同步监视器；Lock需要手动的启动同步（lock()），同时结束同步也需要手动的实现（unlock()）

1. 优先使用顺序：

Lock → 同步代码块（已经进入了方法体，分配了相应资源）→ 同步方法（在方法体之外）

例子：



```java
import java.util.concurrent.locks.ReentrantLock;

class Window implements Runnable{

    private int ticket = 100;
    //1.实例化ReentrantLock
    private ReentrantLock lock = new ReentrantLock();

    @Override
    public void run() {
        while(true){
            try{

                //2.调用锁定方法lock()
                lock.lock();

                if(ticket > 0){

                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }

                    System.out.println(Thread.currentThread().getName() + "：售票，票号为：" + ticket);
                    ticket--;
                }else{
                    break;
                }
            }finally {
                //3.调用解锁方法：unlock()
                lock.unlock();
            }

        }
    }
}

public class LockTest {
    public static void main(String[] args) {
        Window w = new Window();

        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("窗口1");
        t2.setName("窗口2");
        t3.setName("窗口3");

        t1.start();
        t2.start();
        t3.start();
    }
}
```

**总结**：

1. 实例化ReentrantLock：`private ReentrantLock lock = new ReentrantLock();`
2. 调用锁定方法lock()：`lock.lock();`
3. 调用解锁方法：unlock()`lock.unlock();`

## 创建线程的方式三：实现Callable接口。 --- JDK 5.0新增

如何理解实现Callable接口的方式创建多线程比实现Runnable接口创建多线程方式强大？

1. call()可以有返回值的。
2. call()可以抛出异常，被外面的操作捕获，获取异常的信息
3. Callable是支持泛型的

例子：

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

//1.创建一个实现Callable的实现类
class NumThread implements Callable{
    //2.实现call方法，将此线程需要执行的操作声明在call()中
    @Override
    public Object call() throws Exception {
        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            if(i % 2 == 0){
                System.out.println(i);
                sum += i;
            }
        }
        return sum;
    }
}


public class ThreadNew {
    public static void main(String[] args) {
        //3.创建Callable接口实现类的对象
        NumThread numThread = new NumThread();
        //4.将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象
        FutureTask futureTask = new FutureTask(numThread);
        //5.将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()
        new Thread(futureTask).start();

        try {
            //6.获取Callable中call方法的返回值
            //get()返回值即为FutureTask构造器参数Callable实现类重写的call()的返回值。
            Object sum = futureTask.get();
            System.out.println("总和为：" + sum);
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (ExecutionException e) {
            e.printStackTrace();
        }
    }

}
```

**总结**：

1. 创建一个实现Callable的实现类`class NumThread implements Callable{}`
2. 实现call方法，将此线程需要执行的操作声明在call()中`public Object call() throws Exception {}`
3. 创建Callable接口实现类的对象`NumThread numThread = new NumThread()`
4. 将此Callable接口实现类的对象作为传递到FutureTask构造器中，创建FutureTask的对象`FutureTask futureTask = new FutureTask(numThread);`
5. 将FutureTask的对象作为参数传递到Thread类的构造器中，创建Thread对象，并调用start()`new Thread(futureTask).start()`
6. 获取Callable中call方法的返回值,用get()返回值即为FutureTask构造器参数Callable实现类重写的call()的返回值。`Object sum = futureTask.get();`

## 创建线程的方式四：使用线程池

好处：

1. 提高响应速度（减少了创建新线程的时间）
2. 降低资源消耗（重复利用线程池中线程，不需要每次都创建）
3. 便于线程管理
    - corePoolSize：核心池的大小
    - maximumPoolSize：最大线程数
    - keepAliveTime：线程没有任务时最多保持多长时间后会终止

代码如下：



```java
class NumberThread implements Runnable{

    @Override
    public void run() {
        for(int i = 0;i <= 100;i++){
            if(i % 2 == 0){
                System.out.println(Thread.currentThread().getName() + ": " + i);
            }
        }
    }
}

class NumberThread1 implements Runnable{

    @Override
    public void run() {
        for(int i = 0;i <= 100;i++){
            if(i % 2 != 0){
                System.out.println(Thread.currentThread().getName() + ": " + i);
            }
        }
    }
}

public class ThreadPool {

    public static void main(String[] args) {
        //1. 提供指定线程数量的线程池
        ExecutorService service = Executors.newFixedThreadPool(10);
        ThreadPoolExecutor service1 = (ThreadPoolExecutor) service;
        //设置线程池的属性
//        System.out.println(service.getClass());
//        service1.setCorePoolSize(15);
//        service1.setKeepAliveTime();


        //2.执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象
        service.execute(new NumberThread());//适合适用于Runnable
        service.execute(new NumberThread1());//适合适用于Runnable

//        service.submit(Callable callable);//适合使用于Callable
        //3.关闭连接池
        service.shutdown();
    }

}
```

**总结**:

1. 提供指定线程数量的线程池`ExecutorService service = Executors.newFixedThreadPool(10);`
2. 执行指定的线程的操作。需要提供实现Runnable接口或Callable接口实现类的对象`service.execute(new NumberThread())`;对于Callable接口，它的语句是`service.submit(Callable callable)`
3. 关闭连接池`service.shutdown();`



# 5、String

## String简介

String:字符串，使用一对""引起来表示。

1.String声明为final的，不可被继承

2.String实现了Serializable接口：表示字符串是支持序列化的。实现了Comparable接口：表示String可以比较大小

3.String内部定义了final char[] value用于存储字符串数据

4.String:代表不可变的字符序列。**简称：不可变性。**

> 体现：
> 1.当对字符串重新赋值时，需要重写指定内存区域赋值，不能使用原有的value进行赋值。
> 2.当对现有的字符串进行连接操作时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值。
> 3.当调用String的replace()方法修改指定字符或字符串时，也需要重新指定内存区域赋值，不能使用原有的value进行赋值。

5.通过字面量的方式（区别于new）给一个字符串赋值，此时的字符串值声明在字符串常量池中。

6.字符串常量池中是不会存储相同内容的字符串的。

## String的实例化方式：

```java
方式一：通过字面量定义的方式
方式二：通过new + 构造器的方式
```

面试题：String s = new String("abc");方式创建对象，在内存中创建了几个对象？

两个:一个是堆空间中new结构，另一个是char[]对应的常量池中的数据："abc"

## 字符串拼接注意点

1. 常量与常量的拼接结果在常量池。且常量池中不会存在相同内容的常量。
2. 只要其中有一个是变量，结果就在堆中。
3. 如果拼接的结果调用intern()方法，返回值就在常量池中

## String 与基本数据类型、包装类之间的转换。

```java
String --> 基本数据类型、包装类：调用包装类的静态方法：parseXxx(str)
基本数据类型、包装类 --> String:调用String重载的valueOf(xxx)
```

## String 与 char[]之间的转换

```java
String --> char[]:调用String的toCharArray()
char[] --> String:调用String的构造器
```

## String 与 byte[]之间的转换

```java
编码：String --> byte[]:调用String的getBytes()
解码：byte[] --> String:调用String的构造器

编码：字符串 -->字节  (看得懂 --->看不懂的二进制数据)
解码：编码的逆过程，字节 --> 字符串 （看不懂的二进制数据 ---> 看得懂）

说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
```

## String内建函数

```
int length()：返回字符串的长度： return value.length
char charAt(int index)： 返回某索引处的字符return value[index]
boolean isEmpty()：判断是否是空字符串：return value.length == 0
String toLowerCase()：使用默认语言环境，将 String 中的所有字符转换为小写
String toUpperCase()：使用默认语言环境，将 String 中的所有字符转换为大写
String trim()：返回字符串的副本，忽略前导空白和尾部空白
boolean equals(Object obj)：比较字符串的内容是否相同
boolean equalsIgnoreCase(String anotherString)：与equals方法类似，忽略大小写
String concat(String str)：将指定字符串连接到此字符串的结尾。 等价于用“+”
int compareTo(String anotherString)：比较两个字符串的大小
String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。
String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。
```

------



```
boolean endsWith(String suffix)：测试此字符串是否以指定的后缀结束
boolean startsWith(String prefix)：测试此字符串是否以指定的前缀开始
boolean startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的子字符串是否以指定前缀开始

boolean contains(CharSequence s)：当且仅当此字符串包含指定的 char 值序列时，返回 true
int indexOf(String str)：返回指定子字符串在此字符串中第一次出现处的索引
int indexOf(String str, int fromIndex)：返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始
int lastIndexOf(String str)：返回指定子字符串在此字符串中最右边出现处的索引
int lastIndexOf(String str, int fromIndex)：返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索

注：indexOf和lastIndexOf方法如果未找到都是返回-1
```

------



```
替换：
String replace(char oldChar, char newChar)：返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。
String replace(CharSequence target, CharSequence replacement)：使用指定的字面值替换序列替换此字符串所有匹配字面值目标序列的子字符串。
String replaceAll(String regex, String replacement)：使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。
String replaceFirst(String regex, String replacement)：使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。
匹配:
boolean matches(String regex)：告知此字符串是否匹配给定的正则表达式。
切片：
String[] split(String regex)：根据给定正则表达式的匹配拆分此字符串。
String[] split(String regex, int limit)：根据匹配给定的正则表达式来拆分此字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。
```

## 关于StringBuffer和StringBuilder的使用

**String、StringBuffer、StringBuilder三者的异同？**

String:不可变的字符序列；底层使用char[]存储

StringBuffer:可变的字符序列；线程安全的，效率低；底层使用char[]存储

StringBuilder:可变的字符序列；jdk5.0新增的，线程不安全的，效率高；底层使用char[]存储



```java
源码分析：
String str = new String();//char[] value = new char[0];
String str1 = new String("abc");//char[] value = new char[]{'a','b','c'};

StringBuffer sb1 = new StringBuffer();//char[] value = new char[16];底层创建了一个长度是16的数组。
System.out.println(sb1.length());//
sb1.append('a');//value[0] = 'a';
sb1.append('b');//value[1] = 'b';

StringBuffer sb2 = new StringBuffer("abc");//char[] value = new char["abc".length() + 16];

//问题1. System.out.println(sb2.length());//3，里面只有3个元素
//问题2. 扩容问题:如果要添加的数据底层数组盛不下了，那就需要扩容底层的数组。
         默认情况下，扩容为原来容量的2倍 + 2，同时将原有数组中的元素复制到新的数组中。

        指导意义：开发中建议大家使用：StringBuffer(int capacity) 或 StringBuilder(int capacity)
```

**StringBuffer的常用方法**：

```java
StringBuffer append(xxx)：提供了很多的append()方法，用于进行字符串拼接
StringBuffer delete(int start,int end)：删除指定位置的内容
StringBuffer replace(int start, int end, String str)：把[start,end)位置替换为str
StringBuffer insert(int offset, xxx)：在指定位置插入xxx
StringBuffer reverse() ：把当前字符序列逆转
public int indexOf(String str)
public String substring(int start,int end):返回一个从start开始到end索引结束的左闭右开区间的子字符串
public int length()
public char charAt(int n )
public void setCharAt(int n ,char ch)
```

总结：

增：append(xxx)

删：delete(int start,int end)

改：setCharAt(int n ,char ch) / replace(int start, int end, String str)

查：charAt(int n )

插：insert(int offset, xxx)

长度：length();

遍历：for() + charAt() / toString()

**对比String、StringBuffer、StringBuilder三者的效率：**

从高到低排列：StringBuilder > StringBuffer > String

# 6、 JDK 8之前日期和时间的API（1）

## JDK 8之前日期和时间的API（2）

一、SimpleDateFormat的使用：SimpleDateFormat对日期Date类的格式化和解析

> 1.两个操作：
>
> > 1.1 格式化：日期 --->字符串(format)
>
> > 1.2 解析：格式化的逆过程，字符串 ---> 日期(parse，注意抛出异常throws ParseException)

> 2.SimpleDateFormat的实例化（按照指定的方式格式化和解析：调用带参的构造器）

二、Calendar日历类(抽象类）的使用

方式一：创建其子类（GregorianCalendar）的对象

```java
System.out.println(calendar.getClass());
```

方式二：调用其静态方法getInstance()

```java
Calendar calendar = Calendar.getInstance();
```

常用方法：

```java
get()
set()
add()
getTime():日历类---> Date
setTime():Date ---> 日历类
```

## jdk 8中日期时间API的测试

## 偏移量

年是从1900年开始的，月份是从0开始的

## LocalDate、LocalTime、LocalDateTime 的使用

1. LocalDateTime相较于LocalDate、LocalTime，使用频率要高
2. 类似于Calendar

> now():获取当前的日期（LocalDate）、时间（LocalTime）、日期+时间（LocalDateTime）
>
> of():设置指定的年、月、日、时、分、秒。没有偏移量

> getXxx():获取相关的属性
>
> > getDayOfMonth()

> > getDayOfWeek()
>
> > getMinute()等

> withXxx():体现不可变性，原来的数据不会改变。
>
> > withDayOfMonth 修改日期

> > withHour 修改小时

## Instanct的使用

Instant:时间线上的一个瞬时点。这可能被用来记录应用程序中的事件时间戳



```
now():获取本初子午线对应的标准时间
atOffset():添加时间偏移量
toEpochMilli():获取自1970年1月1日0时0分0秒（UTC）开始的毫秒数  ---> Date类的getTime()
ofEpochMilli():通过给定的毫秒数，获取Instant实例  -->Date(long millis)
```

## DateTimeFormatter:格式化或解析日期、时间

方式一：预定义的标准格式。如：ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;ISO_LOCAL_TIME

```java
DateTimeFormatter formatter = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
```

方式二：本地化相关的格式。如：ofLocalizedDateTime()

FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT :适用于LocalDateTime

```java
DateTimeFormatter formatter1 = DateTimeFormatter.ofLocalizedDateTime(FormatStyle.LONG);
```

本地化相关的格式。如：ofLocalizedDate()

FormatStyle.FULL / FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT : 适用于LocalDate

```
DateTimeFormatter formatter2 = DateTimeFormatter.ofLocalizedDate(FormatStyle.MEDIUM);
```

重点： 方式三：自定义的格式。如：ofPattern(“yyyy-MM-dd hh:mm:ss”)

```
DateTimeFormatter formatter3 = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm:ss");
```

## CompareTest

一、说明：Java中的对象，正常情况下，只能进行比较：== 或 != 。不能使用 > 或 < 的

但是在开发场景中，我们需要对多个对象进行排序，言外之意，就需要比较对象的大小。

如何实现？使用两个接口中的任何一个：Comparable 或 Comparator

二、Comparable接口与Comparator的使用的对比：

Comparable接口的方式一旦一定，保证Comparable接口实现类的对象在任何位置都可以比较大小。

Comparator接口属于临时性的比较。

Comparable接口的使用举例： 自然排序

1. 像String、包装类等实现了Comparable接口，重写了compareTo(obj)方法，给出了比较两个对象大小的方式。

2. 像String、包装类重写compareTo()方法以后，进行了从小到大的排列

3. 重写compareTo(obj)的规则：

    如果当前对象this大于形参对象obj，则返回正整数，

    如果当前对象this小于形参对象obj，则返回负整数，

    如果当前对象this等于形参对象obj，则返回零。

4. 对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，重写compareTo(obj)方法。在compareTo(obj)方法中指明如何排序

Comparator接口的使用：定制排序

1. 背景：
    当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，或者实现了java.lang.Comparable接口的排序规则不适合当前的操作，那么可以考虑使用 Comparator 的对象来排序.
2. 重写compare(Object o1,Object o2)方法，比较o1和o2的大小：

> 如果方法返回正整数，则表示o1大于o2；

> 如果返回0，表示相等；

> 返回负整数，表示o1小于o2。





# 7、枚举类

## 枚举类

一、枚举类的使用

1. 枚举类的理解：类的对象只有有限个，确定的。我们称此类为枚举类
2. 当需要定义一组常量时，强烈建议使用枚举类
3. 如果枚举类中只有一个对象，则可以作为单例模式的实现方式。

二、如何定义枚举类

方式一：jdk5.0之前，自定义枚举类

方式二：jdk5.0，可以使用enum关键字定义枚举类

三、Enum类中的常用方法：

values()方法：返回枚举类型的对象数组。该方法可以很方便地遍历所有的枚举值。

valueOf(String str)：可以把一个字符串转为对应的枚举类对象。要求字符串必须是枚举类对象的“名字”。如不是，会有运行时异常：IllegalArgumentException。

toString()：返回当前枚举类对象常量的名称

四、使用enum关键字定义的枚举类实现接口的情况

> 情况一：实现接口，在enum类中实现抽象方法
>
> 情况二：让枚举类的对象分别实现接口中的抽象方法

自定义枚举类：

1. 声明对象的属性：private final修饰
2. 私有化类的构造器，并给对象属性赋值
3. **提供当前枚举类的多个对象：public static final的**
4. 其他诉求，如获取枚举类对象的属性（getXxx方法）或者提供toString（）

使用enum关键字定义枚举类
说明：定义的枚举类默认继承于java.lang.Enum类

1. 提供当前枚举类的对象，多个对象之间用","隔开，末尾对象";"结束
2. 声明对象的属性:private final修饰
3. 私有化类的构造器,并给对象属性赋值
4. 其他诉求，如获取枚举类对象的属性（getXxx方法）或者提供toString（）

# 8、注解的使用

1. 理解Annotation:
    ① jdk 5.0 新增的功能
    ② Annotation 其实就是代码里的特殊标记, 这些标记可以在编译, 类加载, 运行时被读取, 并执行相应的处理。通过使用 Annotation,程序员可以在不改变原有逻辑的情况下, 在源文件中嵌入一些补充信息。
    ③在JavaSE中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在JavaEE/Android中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替JavaEE旧版中所遗留的繁冗代码和XML配置等。
2. Annocation的使用示例

- 示例一：生成文档相关的注解
- 示例二：在编译时进行格式检查(JDK内置的三个基本注解)

@Override: 限定重写父类方法, 该注解只能用于方法
@Deprecated: 用于表示所修饰的元素(类, 方法等)已过时。通常是因为所修饰的结构危险或存在更好的选择
@SuppressWarnings: 抑制编译器警告

- 示例三：跟踪代码依赖性，实现替代配置文件功能

1. 如何自定义注解：参照@SuppressWarnings定义
    ① 注解声明为：@interface
    ② 内部定义成员，通常使用value表示
    ③ 可以指定成员的默认值，使用default定义
    ④ 如果自定义注解没有成员，表明是一个标识作用。
    如果注解有成员，在使用注解时，需要指明成员的值。
    自定义注解必须配上注解的信息处理流程(使用反射)才有意义。
    自定义注解通过都会指明两个元注解：Retention、Target
2. jdk 提供的4种元注解

元注解：对现有的注解进行解释说明的注解

Retention：指定所修饰的 Annotation 的生命周期：SOURCE\CLASS（默认行为）\RUNTIME，只有声明为RUNTIME生命周期的注解，才能通过反射获取。
Target:用于指定被修饰的 Annotation 能用于修饰哪些程序元素

----------出现的频率较低---------

Documented:表示所修饰的注解在被javadoc解析时，保留下来。
Inherited:被它修饰的 Annotation 将具有继承性。

1. 通过反射获取注解信息 ---到反射内容时系统讲解
2. jdk 8 中注解的新特性：可重复注解、类型注解

6.1 可重复注解：
① 在MyAnnotation上声明@Repeatable，成员值为MyAnnotations.class
② MyAnnotation的Target和Retention等元注解与MyAnnotations相同。

6.2 类型注解：
ElementType.TYPE_PARAMETER 表示该注解能写在类型变量的声明语句中（如：泛型声明）。
ElementType.TYPE_USE 表示该注解能写在使用类型的任何语句中。

# 9、集合框架的概述

1.集合、数组都是对多个数据进行存储操作的结构，简称Java容器。
说明：此时的存储，主要指的是内存层面的存储，不涉及到持久化的存储（.txt,.jpg,.avi，数据库中）

2.1 数组在存储多个数据方面的特点：

> 一旦初始化以后，其长度就确定了。
> 数组一旦定义好，其元素的类型也就确定了。我们也就只能操作指定类型的数据了。 比如：String[] arr;int[] arr1;Object[] arr2;

2.2 数组在存储多个数据方面的缺点：

> 一旦初始化以后，其长度就不可修改。
> 数组中提供的方法非常有限，对于添加、删除、插入数据等操作，非常不便，同时效率不高。
> 获取数组中实际元素的个数的需求，数组没有现成的属性或方法可用
> 数组存储数据的特点：有序、可重复。对于无序、不可重复的需求，不能满足。

二、集合框架
|----Collection接口：单列集合，用来存储一个一个的对象
　　|----List接口：存储有序的、可重复的数据。 -->“动态”数组
　　　　|----ArrayList、LinkedList、Vector

　　|----Set接口：存储无序的、不可重复的数据 -->高中讲的“集合”
　　　　|----HashSet、LinkedHashSet、TreeSet

|----Map接口：双列集合，用来存储一对(key - value)一对的数据 -->高中函数：y = f(x)
　　　　|----HashMap、LinkedHashMap、TreeMap、Hashtable、Properties

三、Collection接口中的方法的使用

- add(Object e):将元素e添加到集合coll中
- size():获取添加的元素的个数
- addAll(Collection coll1):将coll1集合中的元素添加到当前的集合中
- clear():清空集合元素
- isEmpty():判断当前集合是否为空



## Collection接口中声明的方法的测试

向Collection接口的实现类的对象中添加数据obj时，要求obj所在类要重写equals().

1. contains(Object obj):判断当前集合中是否包含obj
2. containsAll(Collection coll1):判断形参coll1中的所有元素是否都存在于当前集合中。
3. remove(Object obj):从当前集合中移除obj元素。
4. removeAll(Collection coll1):差集：从当前集合中移除coll1中所有的元素。
5. retainAll(Collection coll1):交集：获取当前集合和coll1集合的交集，并返回给当前集合
6. equals(Object obj):要想返回true，需要当前集合和形参集合的元素都相同。
7. hashCode():返回当前对象的哈希值
8. 集合 --->数组：toArray()（拓展：数组 --->集合:调用Arrays类的静态方法asList()）
9. iterator():返回Iterator接口的实例，用于遍历集合元素。

注意：



```
List arr1 = Arrays.asList(new int[]{123, 456});
System.out.println(arr1.size());//1

List arr2 = Arrays.asList(new Integer[]{123, 456});
System.out.println(arr2.size());//2
```

## 集合元素的遍历操作，使用迭代器Iterator接口

1.内部的方法：hasNext() 和 next()

推荐的方式：



```
//hasNext():判断是否还有下一个元素
while(iterator.hasNext()){
    //next():①指针下移 ②将下移以后集合位置上的元素返回
    System.out.println(iterator.next());
}
```

2.集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。

注意两种错误方式：



```
//错误方式一：
Iterator iterator = coll.iterator();
while((iterator.next()) != null){
    System.out.println(iterator.next());
}
```

解析：while中的iterator.next()已经返回来集合中第一个数，接着输出语句中的iterator.next()打印了集合中的第二个元素。然后又回到while中的iterator.next()，如此往复，知道遍历完毕。打印的结果都是隔一个元素打印，并且最后会报错，越界。



```
//错误方式二：
//集合对象每次调用iterator()方法都得到一个全新的迭代器对象，默认游标都在集合的第一个元素之前。
while (coll.iterator().hasNext()){
    System.out.println(coll.iterator().next());
}
```

解析：每次调用iterator()方法都得到一个全新的迭代器对象，每次都是打印集合第一个元素，并且是死循环。

3.内部定义了remove(),可以在遍历的时候，删除集合中的元素。此方法不同于集合直接调用remove()

## jdk 5.0 新增了foreach循环，用于遍历集合、数组



```
public void test1(){
    Collection coll = new ArrayList();
    coll.add(123);
    coll.add(456);
    coll.add(new Person("Jerry",20));
    coll.add(new String("Tom"));
    coll.add(false);

    //for(集合元素的类型 局部变量 : 集合对象)
    //内部仍然调用了迭代器。
    for(Object obj : coll){
        System.out.println(obj);
    }
}
```

## List接口

1.List接口框架

|----Collection接口：单列集合，用来存储一个一个的对象
　　|----List接口：存储有序的、可重复的数据。 -->“动态”数组,替换原有的数组
　　　　|----ArrayList：作为List接口的主要实现类；线程不安全的，效率高；底层使用Object[] elementData存储
　　　　|----LinkedList：对于频繁的插入、删除操作，使用此类效率比ArrayList高；底层使用双向链表存储
　　　　|----Vector：作为List接口的古老实现类；线程安全的，效率低；底层使用Object[] elementData存储

2.ArrayList的源码分析：

2.1 jdk 7情况下
ArrayList list = new ArrayList();//底层创建了长度是10的Object[]数组elementData
list.add(123);//elementData[0] = new Integer(123);
...
list.add(11);//如果此次的添加导致底层elementData数组容量不够，则扩容。
默认情况下，扩容为原来的容量的1.5倍，同时需要将原有数组中的数据复制到新的数组中。

结论：建议开发中使用带参的构造器：ArrayList list = new ArrayList(int capacity)

2.2 jdk 8中ArrayList的变化：
ArrayList list = new ArrayList();//底层Object[] elementData初始化为{}.并没有创建长度为10的数组

list.add(123);//第一次调用add()时，底层才创建了长度10的数组，并将数据123添加到elementData[0]，后续的添加和扩容操作与jdk 7 无异。

2.3 小结：jdk7中的ArrayList的对象的创建类似于单例的饿汉式，而jdk8中的ArrayList的对象的创建类似于单例的懒汉式，延迟了数组的创建，节省内存。

3.LinkedList的源码分析：
LinkedList list = new LinkedList(); 内部声明了Node类型的first和last属性，默认值为null

list.add(123);//将123封装到Node中，创建了Node对象。

其中，Node定义为：体现了LinkedList的双向链表的说法



```
private static class Node<E> {
     E item;
     Node<E> next;
     Node<E> prev;

     Node(Node<E> prev, E element, Node<E> next) {
     this.item = element;
     this.next = next;
     this.prev = prev;
     }
 }
```

4.Vector的源码分析：jdk7和jdk8中通过Vector()构造器创建对象时，底层都创建了长度为10的数组。在扩容方面，默认扩容为原来的数组长度的2倍。

面试题：ArrayList、LinkedList、Vector三者的异同？
同：三个类都是实现了List接口，存储数据的特点相同：存储有序的、可重复的数据
不同：见上

5.List接口中的常用方法

void add(int index, Object ele):在index位置插入ele元素
boolean addAll(int index, Collection eles):从index位置开始将eles中的所有元素添加进来
Object get(int index):获取指定index位置的元素
int indexOf(Object obj):返回obj在集合中首次出现的位置。如果不存在，返回-1.
int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置。如果不存在，返回-1.
Object remove(int index):移除指定index位置的元素，并返回此元素
Object set(int index, Object ele):设置指定index位置的元素为ele
List subList(int fromIndex, int toIndex):返回从fromIndex到toIndex位置的子集合

总结：常用方法
增：add(Object obj)
删：remove(int index) / remove(Object obj)
改：set(int index, Object ele)
查：get(int index)
插：add(int index, Object ele)
长度：size()
遍历：
① Iterator迭代器方式
② 增强for循环
③ 普通的循环

注意：区分List中remove(int index)和remove(Object obj)



```
public void testListRemove() {
    List list = new ArrayList();
    list.add(1);
    list.add(2);
    list.add(3);
    updateList(list);
    System.out.println(list);//
}

private void updateList(List list) {
    //list.remove(2);
    list.remove(new Integer(2));
}
```

分析：第一条语句`list.remove(2);`中2是index，所以移除的是索引为2的元素，它是list的remove(int index)；
第二条语句`list.remove(new Integer(2));`中的2是对象，所以移除的是内容为2的元素，它是list的remove(Object obj)。

## set接口

1. Set接口的框架：

|----Collection接口：单列集合，用来存储一个一个的对象
　　|----Set接口：存储无序的、不可重复的数据 -->高中讲的“集合”
　　　　|----HashSet：作为Set接口的主要实现类；线程不安全的；可以存储null值
　　　　|----LinkedHashSet：作为HashSet的子类；遍历其内部数据时，可以按照添加的顺序遍历，对于频繁的遍历操作，LinkedHashSet效率高于HashSet.
　　　　|----TreeSet：可以按照添加对象的指定属性，进行排序。

一、Set：存储无序的、不可重复的数据
以HashSet为例说明：
1.无序性：不等于随机性。存储的数据在底层数组中并非按照数组索引的顺序添加，而是根据数据的**哈希值**决定的。

2.不可重复性：保证添加的元素按照equals()判断时，不能返回true.即：相同的元素只能添加一个。

二、添加元素的过程：以HashSet为例：
我们向HashSet中添加元素a,首先调用元素a所在类的hashCode()方法，计算元素a的哈希值，此哈希值接着通过某种算法计算出在HashSet底层数组中的存放位置（即为：索引位置），判断数组此位置上是否已经有元素：
如果此位置上没有其他元素，则元素a添加成功。 --->情况1
如果此位置上有其他元素b(或以链表形式存在的多个元素），则比较元素a与元素b的hash值：
　　如果hash值不相同，则元素a添加成功。--->情况2
　　如果hash值相同，进而需要调用元素a所在类的equals()方法：
　　　　equals()返回true,元素a添加失败
　　　　equals()返回false,则元素a添加成功。--->情况2

对于添加成功的情况2和情况3而言：元素a 与已经存在指定索引位置上数据以链表的方式存储。
jdk 7 :元素a放到数组中，指向原来的元素。
jdk 8 :原来的元素在数组中，指向元素a
总结：七上八下

HashSet底层：数组+链表的结构。

------

1. Set接口中没有额外定义新的方法，使用的都是Collection中声明过的方法。
2. 要求：向Set(主要指：HashSet、LinkedHashSet)中添加的数据，其所在的类一定要重写hashCode()和equals()
    要求：重写的hashCode()和equals()尽可能保持一致性：相等的对象必须具有相等的散列码
    重写两个方法的小技巧：对象中用作 equals() 方法比较的 Field，都应该用来计算 hashCode 值。

## TreeSet

1. 向TreeSet中添加的数据，要求是相同类的对象。
2. 两种排序方式：自然排序（实现Comparable接口） 和 定制排序（Comparator）
3. 自然排序中，比较两个对象是否相同的标准为：compareTo()返回0.不再是equals().
4. 定制排序中，比较两个对象是否相同的标准为：compare()返回0.不再是equals().



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

~~~ java
import java.io.FileInputStream;
import java.io.IOException;
import java.util.Properties;
public class PropertiesTest {


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

}
~~~



# 10、泛型

## 泛型的使用

1.jdk 5.0新增的特性

2.在集合中使用泛型：

以ArrayList为例：

~~~java
@Test
public void test1(){
    ArrayList<Integer> list = new ArrayList<>();
list.add(78);
list.add(87);
list.add(99);
list.add(65);

//list.add(&quot;Tom&quot;);

Iterator&lt;Integer&gt; iterator = list.iterator();
while (iterator.hasNext()){
    System.out.println(iterator.next());
}

}
~~~

以HashSet为例

~~~java
@Test
public void test2() {
    Map<String, Integer> map = new HashMap<>();

    map.put("Tom", 87);
    map.put("Jerry", 87);
    map.put("Jack", 67);

    //map.put(123, &quot;kkk&quot;);

    //泛型的嵌套
    Set <Map.Entry <String, Integer >> entry = map.entrySet();
    Iterator <Map.Entry <String, Integer >> iterator = entry.iterator();
    while (iterator.hasNext()) {
        Map.Entry <String, Integer > e = iterator.next();
        String key = e.getKey();
        Integer value = e.getValue();
        System.out.println(key + " ----- >" + value);
    }

}
~~~

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

~~~java
public class SubOrder extends Order<Integer> {
public static &lt;E&gt; List&lt;E&gt; copyFromArrayToList(E[] arr){
    ArrayList&lt;E&gt; list = new ArrayList&lt;&gt;();

    for (E e: arr){
        list.add(e);
    }

    return list;
}

}
~~~



那么，由于子类在继承带泛型的父类时，指明了泛型类型。则实例化子类对象时，不再需要指明泛型。

```java
SubOrder sub1 = new SubOrder();
sub1.setOrderT(1122);
```

如果一个子类在继承时未声明类型：

```java
public class SubOrder1<T> extends Order<T> {
}
```

声明时：

```java
SubOrder1<String> sub2 = new SubOrder1<>();
sub2.setOrderT("order2......");
```

泛型不同的引用不能相互赋值。

```java
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

类A是类B的父类，G\<A\>和G\<B\>是没有关系的，二者共同的父类是：G<?>

~~~java
public void test1(){
    List<Object> list1 = null;
    List<String> list2 = null;
List<?> list = null;

list = list1;
list = list2;

System.out.println(list1);
System.out.println(list2);


List<String> list3 = new ArrayList<>();
list3.add("ASA");
list3.add("DGA");
list3.add("Gesag");

//list.add("AA");
//list.add('?');

list.add(null);

//获取(读取)：允许读取数据，读取的数据类型为Object。
Object o = list.get(0);
System.out.println(o);
~~~



# 11、File类与流

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



## 流

一、流的分类：
1.操作数据单位：字节流、字符流
2.数据的流向：输入流、输出流
3.流的角色：节点流、处理流

| 抽象基类 | 字节流       | 字符流 |
| :------- | :----------- | :----- |
| 输入流   | InputStream  | Reader |
| 输出流   | OutputStream | Writer |

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

~~~java
@Test
public void testFileReader1(){
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

}
~~~



读取文件的推荐方式：



```java
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

~~~ java
/*
实现对图片的复制操作
 */
@Test
public void testFileInputOutputStream()  {
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        //
        File srcFile = new File("爱情与友情.jpg");
        File destFile = new File("爱情与友情2.jpg");
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
}
~~~

## 处理流之一：缓冲流的使用

1.缓冲流：

- BufferedInputStream
- BufferedOutputStream
- BufferedReader
- BufferedWriter

2.作用：提高流的读取、写入的速度

提高读写速度的原因：内部提供了一个缓冲区

3.处理流，就是“套接”在已有的流的基础上。

说明：

① 关闭外层流的同时，内层流也会自动的进行关闭。关于内层流的关闭，我们可以省略.

② 使用String读取数据：



```java
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

~~~java
//实现文件复制的方法
public void copyFileWithBuffered(String srcPath,String destPath){
    BufferedInputStream bis = null;
    BufferedOutputStream bos = null;
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

}
~~~

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

~~~java
/*
此时处理异常的话，仍然应该使用try-catch-finally
综合使用InputStreamReader和OutputStreamWriter

*/

@Test

public void test2() throws Exception {

//1.造文件、造流

File file1 = new File("dbcp.txt");

File file2 = new File("dbcp_gbk.txt");


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

}
~~~

## Path

1. jdk 7.0 时，引入了 Path、Paths、Files三个类。

2. 此三个类声明在：java.nio.file包下。

3. Path可以看做是java.io.File类的升级版本。也可以表示文件或文件目录，与平台无关

4. 如何实例化Path:使用Paths.

    `static Path get(String first, String … more)` : 用于将多个字符串串连成路径
    `static Path get(URI uri)`: 返回指定uri对应的Path路径

**如何使用Paths实例化Path**

示例代码：

~~~java
@Test
public void test1() {
    Path path1 = Paths.get("d:\\nio\\hello.txt");//new File(String filepath)
Path path2 = Paths.get(&quot;d:\\&quot;, &quot;nio\\hello.txt&quot;);//new File(String parent,String filename);

System.out.println(path1);
System.out.println(path2);

Path path3 = Paths.get(&quot;d:\\&quot;, &quot;nio&quot;);
System.out.println(path3);

}
~~~

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



```java
File file = path1.toFile();//Path--->File的转换
Path newPath = file.toPath();//File--->Path的转换
```

## Files工具类的使用：操作文件或目录的工具类

以这两条代码为例，导入文件路径：

```java
Path path1 = Paths.get("d:\\nio", "hello.txt");
Path path2 = Paths.get("atguigu.txt");
```

`Path copy(Path src, Path dest, CopyOption … how)`: 文件的复制
说明要想复制成功，要求path1对应的物理上的文件存在。path1对应的文件没有要求。

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

```java
Path path4 = Paths.get("d:\\nio\\hi.txt");
Files.createFile(path4);
```

`void delete(Path path)` : 删除一个文件/目录，如果不存在，执行报错

```java
Files.delete(path4);
```

`void deleteIfExists(Path path)`: Path对应的文件/目录如果存在，执行删除.如果不存在，正常执行结束

```java
Files.deleteIfExists(path3);
```

`Path move(Path src, Path dest, CopyOption…how)`: 将 src 移动到 dest 位置
说明：要想执行成功，src对应的物理上的文件需要存在，dest对应的文件没有要求。

```java
Files.move(path1, path2, StandardCopyOption.ATOMIC_MOVE);
```

`long size(Path path)`: 返回 path 指定文件的大小

```java
long size = Files.size(path2);
System.out.println(size);
```

`boolean exists(Path path, LinkOption … opts)`: 判断文件是否存在

```java
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

```java
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

~~~java
/**
 * Person需要满足如下条件，方可实现序列化：
 * 1.需要实现接口：Serializable
 * 2.当前类提供一个全局常量：serialVersionUID
 * 3.除了当前Person类需要实现Serializable接口之外，还必须保证其内部所有属性
 * 也必须是可序列化的。（默认情况下，基本数据类型可序列化）
 * 补充：ObjectOutputStream和ObjectInputStream不能序列化static和transient修饰的成员变量
 *
 * @author shkstart
 * @create 2019 上午 10:38
 */
public class Person implements Serializable {
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
                "name='" + name + '' ' +
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
        this.name = name;
        this.age = age;
    }

    public Person() {
    }
}

class Account implements Serializable {
    public static final long serialVersionUID = 4754534532L;
    private double balance;

    @Override
    public String toString() {
        return "Account{" +
                "balance=" + balance +
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
}
~~~

4.序列化机制：
对象序列化机制允许把内存中的Java对象转换成平台无关的二进制流，从而允许把这种二进制流持久地保存在磁盘上，或通过网络将这种二进制流传输到另一个网络节点。当其它程序获取了这种二进制流，就可以恢复成原来的Java对象。

## RandomAccessFile的使用

1. RandomAccessFile直接继承于java.lang.Object类，实现了DataInput和DataOutput接口
2. RandomAccessFile既可以作为一个输入流，又可以作为一个输出流
3. 如果RandomAccessFile作为输出流时，写出到的文件如果不存在，则在执行过程中自动创建。如果写出到的文件存在，则会对原有文件内容进行覆盖。（默认情况下，从头覆盖）
4. 可以通过相关的操作，实现RandomAccessFile“插入”数据的效果

示例代码：

~~~java
/*
       使用RandomAccessFile实现数据的插入效果
   */
public void test3() throws IOException {
    RandomAccessFile raf1 = new RandomAccessFile( " hello.txt"," rw");

    raf1.seek(3);//将指针调到角标为3的位置
    //保存指针3后面的所有数据到StringBuilder中
    StringBuilder builder = new StringBuilder((int) new File( " hello.txt").length());
    byte[] buffer = new byte[20];
    int len;
    while ((len = raf1.read(buffer)) != -1) {
        builder.append(new String(buffer, 0, len));
    }
    //调回指针，写入“xyz”
    raf1.seek(3);
    raf1.write( " xyz ".getBytes());

    //将StringBuilder中的数据写入到文件中
    raf1.write(builder.toString().getBytes());

    raf1.close();

}
~~~

