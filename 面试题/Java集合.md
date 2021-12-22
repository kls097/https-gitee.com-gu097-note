# 常用的集合类有哪些？

Map接口和Collection接口是所有集合框架的父接口：
1、Collection 接口的子接口包括Set 接口和List 接口
2、Map接口的实现类主要有HashMap、TreeMap 、Hashtable 、
ConcurrentHashMap 以及Properties 等
3、Set 接口的实现类主要有HashSet、TreeSet 、LinkedHashSet 等
4、List 接口的实现类主要有Arraylist、Linkedlist 、Stack 以及Vector 等

# 集合框架底层数据结构

- List接口
    - ArrayList底层是Object[]数组
    - Vector底层是Object数组
    - LinkedList底层是双向链表，1.6前为循环，1.7取消了循环
- Set接口
    - HashSet（无序唯一）:底层是HashMap
    - LinkedHashSet:底层是LinkedHashMap
    - TreeSet（有序唯一）：底层是红黑树
- Map接口
    - HashMap：1.8之前是数组+链表；1.8以后链表达到一定长度之后转化为红黑树
    - LinkedHashMap:在HashMap底层数据结构的基础上增加了一条双向链表
    - Hashtable:数组+链表
    - TreeMap:红黑树

# 哪些集合是线程不安全的？如何解决？

线程不安全的有Arraylist ,LinkedList,Hashmap,HashSet,TreeSet,TreeMap，PriorityQueue

线程安全的有Vector、hashTable、ConcurrentHashMap

解决方法是使用线程安全的集合类

- ConcurrentHashMap：线程安全的HashMap
- CopyOnWriteArrayList:线程安全的ArrayLIst
- ConcurrentLinkedQueue:线程安全的LinkedList
- BlockingQueue阻塞队列
- ConcurrentSkipListMap：跳表的实现

# Java 集合的快速失败机制”fail-fast" ?

是java 集合的一种错误检测机制， 当多个线程对集合进行结构上的改变的操作
时， 有可能会产生fail -fast 机制。

> 例如

假设存在两个线程（线程1 、线程2) ， 线程1通过Iterator 在遍历集合
A 中的元素， 在某个时候线程2修改了集合A 的结构（是结构上面的修改，而
不是简单的修改集合元素的内容）， 那么这个时候程序就会抛出异常从而产生快速失败机制。

> 原因

迭代器在遍历时直接访问集合中的内容， 并且在遍历过程中使用—个
modCount 变量。集合在被遍历期间如果内容发生变化， 就会改变modCount
的值。每当迭代器使用hashNext（）/next（）遍历下一个元素之前， 都会检测
modCount 变量是否为expectedmodCount 值， 是的话就返回遍历； 否则抛
出异常， 终止遍历。

> 解决办法

1. 在遍历过程中， 所有涉及到改变modCount 值得地方全部加上
    synchronized。
2. 使用线程安全的集合

# 怎么确保一个集合不能被修改？

可以使用Collections. unmodifiableCollection(Collectionc) 方法来创建一个只读集合，这样任何改变集合的操作都会抛出异常。

# 迭代器Iterator 是什么？Iterator 怎么使用？ 有什么特点？

Iterator 接口提供遍历任何Collection 的接口，因为所有Collection 接继承了Iterator迭代器

示例代码如下：



```
List<String> list = new ArrayList<>();
Iterator<String> it = list.iterator();
while(it.hashNext()){
	String obj = it.next();
	System.out.println(obj):
}
```

Iterator 的特点是只能单向遍历， 但是更加安全， 因为它可以确保， 在当前遍历的集合元素被更改的时候， 就会抛出异常。

# 如何边遍历边移除Collection 中的元素？

Iterator.remove()



```
Iterator<Integer> it = list.iterator();
while(it.hashNext()){
	//do something
	it.remove();
}
```

# Iterator 和Listlterator 有什么区别？

- Iterator 可以遍历Set 和List 集合，而ListIterator 只能遍历List。
- Iterator 只能单向遍历，而ListIterator 可以双向遍历（向前／后遍历）。
- ListIterator 实现Iterator 接口，然后添加了一些额外的功能，比如添加一个元素、替换一个元素、获取前面或后面元素的索引位置。

# 遍历一个List 有哪些不同的方式？

for ,Iterator, foreach

# 说一下Arraylist 的优缺点

优点

- Arraylist 底层以数组实现，是一种随机访问模式。Arraylist 实现了Random Access 接口， 因此查找的时候非常快。
- Arraylist 在顺序添加—个元素的时候非室方便。

缺点

- 删除元素的时候， 需要做一次元素复制操作。如果要复制的元素很多， 那么就会比较耗费性能。
- 插入元素的时候， 也需要做一次元素复制操作， 缺点同上。

Arraylist 比较适合顺序添加、随机访问的场景。

# 如何实现数组和List 之间的转换？

数组转List 使用Arrays. aslist(array) 进行转换。

List 转数组：使用List 自带的toArrayQ 方法。

# ArrayList和LinkedList区别？

- 线程都不安全
- ArrayList底层是Object数组，LinkedList底层是双向链表（1.6之前为循环，1.7之后取消了循环）。
- ArrayList指定位置的插入和删除复杂度是O(n-i),LinkedList指定位置的插入复杂度是O(1)，删除复杂度是O(n)。
- ArrayList支持快速随机访问，list.get(i)。LinkedList不支持快速随机访问
- ArrayList的空间浪费体现在预留的容量，LinkedList的空间花费体现在每一个元素都比ArrayList要占用更多的空间

综合来说， 在需要频繁读取集合中的元素时， 更推荐使用ArrayList , 而在插入和删除操作较多时， 更推荐使用LinkedList。

# ArrayList和Vector区别？

底层都是Object数组，ArrayList线程不安全，Vector线程安全

# 插入数据时， ArrayList. LinkedList、Vector 谁速度较快？阐述Arraylist、Vector、LinkedList 的存储性能和特性？

- Arraylist 和Vector 底层的实现都是使用数组方式存储数据。数组元素数大于实际存储的数据以便增加和插入元素， 它们都允许直接按顺序索引元素， 但是插入元素要涉及数组元素移动等内存操作， 所以索引数据快而插入数据慢。
- Vector 中的方法由于加了synchronized 修饰， 因此Vector 是线程安全容器，但性能上较ArrayList 差。
- LinkedList 使用双向链表实现存储， 按序号索引数据需要进行前向或后向遍历，但插入数据时只需要记录当前项的前后项即可， 所以LinkedList插入速度较快。

# 多线程场景下如何使用Arraylist?

Arraylist 不是线程安全的， 如杲遇到多线程场景， 可以通过Collections 的synchronizedList 方法将其转换成线程安全的容器后再使用。

# List和Set的区别?

- List可以包含重复元素，而Set包含唯一项。
- List是一个有序集合，它维护插入顺序，而Set是一个无序集合，不保留插入顺序。
- List接口可以允许n个null值，而Set接口只允许一个null值。
- Set 检索元素效率低下， 删除和插入效率高， 插入和删除不会引起元素位置改变。
- List: 和数组类似， List 可以动态增长， 查找元素效率高， 插入删除元素效率低， 因为会引起其他元素位置改变

# 说一下HashSet 的实现原理？

HashSet 是基于HashMap 实现的， HashSet 的值存放于HashMap 的key
上，HashMap 的value 统一为present, 因此HashSet的实现比较简单， 相关HashSet的操作， 基本上都是直接调用底层HashMap 的相关方法来完成，HashSet 不允许重复的值。

# HashSet 如何检查重复？ HashSet 是如何保证数据不可重复的？

- 向HashSet 中add() 元素时， 判断元素是否存在的依据， 不仅要比较hash 值，同时还要结合equles 方法比较。
- HashSet 中的add()方法会使用HashM ap 的put()方法。
- HashMap 的key 是唯一的，HashSet添加进去的值就是作为HashMap 的key, 并且在HashMap中如果K/V 相同时， 会用新的V 覆盖掉旧的V , 然后返回旧的V。所以不会重复。

# HashSet、LinkedHashSet和TreeSet三者异同

HashSet不能按照添加的顺序遍历，LinkedHashSet和TreeSet可以按照添加的顺序遍历，TreeSet还可以定制排序

# 什么是Hash 算法

哈希算法是指把任意长度的二进制映射为固定长度的较小的二进制值，这个较小
的二进制值叫做哈希值。

# 什么是TreeMap

- TreeMap 是一个有序的key-value 集合， 它是通过红黑树实现的。
- TreeMap 是线程非同步的。
- 实现了排序，按照其键的自然顺序进行排序，或者根据映射是提供的comparetor进行排序，具体取决于构造方法

# 如何决定使用HashMap 还是TreeMap?

平常可以选着hashmap，但是需要对一个有序的key集合时使用TreeMap更好

# Array（数组） 和ArrayList 有何区别？

- Array 可以存储基本数据类型和对象， ArrayList只能存储对象。
- Array 是指定固定大小的，而ArrayList 大小是自动扩展的。
- Array内置方法没有ArrayList多（如addAll、removeAll等）

# comparable 和comparator的区别？

- comparable接口出自java.lang包，它有一个compareTo(Object obj)方法用来排序
- comparator接口出自java.util包，它有一个compare(Object obj1 Object obj2) 方法用来排序

然后根据开发情况选择

# Collection 和Collections 有什么区别？

- java.util.Collection 是一个集合接口（集合类的一个顶级接口） 。它提供了对集合对象进行基本操作的通用接口方法
- Collections 则是集合类的—个工具类／帮助类， 其中提供了一系列静态方法，用于对集合中元素进行排序、搜索以及线程安全等各种操作。**但效率不高。**
- 