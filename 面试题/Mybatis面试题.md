# MyBatis 编程步骤

1. 创建 SqlSessionFactory 对象。
2. 通过 SqlSessionFactory 获取 SqlSession 对象。
3. 通过 SqlSession 获得 Mapper 代理对象。
4. 通过 Mapper 代理对象，执行数据库操作。
5. 执行成功，则使用 SqlSession 提交事务。
6. 执行失败，则使用 SqlSession 回滚事务。
7. 最终，关闭会话。

# MyBatis 的工作原理

- 读取MyBatis配置文件mybatis-config.xml
- 加载映射文件；
- 构造会话工厂SqlsessionFactory；
- 创建会话对象，sqlsession对象；
- Executor 执行器：根据sqlsession对象生成sql语句
- MappedStatement 对象：存储sql语句参数
- 输入参数映射
- 输出结果映射

# mybatis功能架构

- api接口层：提供给外部使用的接口
- 数据处理层：完成一次sql操作
- 基础支撑层：完成连接管理、事务管理、缓存处理、配置加载等基础支撑

# 为什么使用预编译

- 优化sql，因为越复杂的sql编译越复杂
- 防止sql注入问题发生

# Mybatis 的Xml 映射文件中， 不同的Xml映射文件， id是否可以重复？

- 配置了namespace就可以
- 原因就是：namespace + id 是作为key使用的，如果没有namespace就只剩id，容易造成数据覆盖

# Mybatis 是如何将sql 执行结果封装为目标对象并返回的？都有哪些映射形式？

1. 标签逐一定义列名和对象属性名之间的映射关系
2. sql列的别名功能
    - mybatis通过反射创建对象，给对象的属性逐一赋值并返回

# Mybatis 是否可以映射Enum 枚举类？

可以，

- 方法是：自定义一个TypeHandler , 实现TypeHandler 的 setParameter（）和getResult（） 接口方法。

# MyBatis 如何执行批量插入?

首先， 创建一个简单的insert 语句：



```
<insert id=" insertname" >
    insert into names (name) values (#{value})
</insert>
```

然后在java 代码中像下面这样执行批处理插入：



```
list < string > names = new arraylist（）;
names.add("fred");
names.add("barney");
names.add("betty");
names.add("wilma");
sqlsession sqlsession =sqlsessionfactory.opensession(executortype.batch);
try {
namemapper mapper = sqlsession.getmapper(namemapper.class);
for (string name: names) {
mapper.insertname(name);
}
sqlsession.commit();
} catch (Exception e) {
e.printStackTrace（）;
sqlSession.rollback（）;
throw e;
}
finally {
sqlsession.close();
}
```



# Mybatis 是如何进于分页的？分页插件的原理是什么？

Mybatis使用RowBounds 对象进行分页， 它是针对ResultSet 结果组执行的内存分页，而非物理分页。可以在sql 内直接书写带有物理分页的参数来完成物理分页功能，也可以使用分页插件来完成物理分页．

分页插件的基本原理是使用Mybatis 提供的插件接口，实现自定义插件，在插件的拦截方法内拦截待执行的sql, 然后重写sql, 根据dialect 方言，添加对应的物理分页语句和物理分页参数。

# 模糊查询like 语句该怎么写？

第1种：在Java 代码中添加sql 通配符．



```
string wildcardname = "%smi%" ;
list<name> names = mapper.selectlike(wildcardname);
<select id=" selectlike" >
select * from foo where bar like #{value}
</select>
```



第2种：在sql 语句中拼接通配符，但会引起sql 注入



```
string wildcardname = "smi" ;
list<name> names = mapper.selectlike(wildcardname);
<select id=" selectlike">
select * from foo where bar like %#{value}%
</select>
```



# #{}和＄{}的区别是什么？

1. \#{}是预编译处理，＄{}是字符串替换。
2. Mybatis 在处理#{}时， 会将sql 中的#{}替换为？号， 调用PreparedStatement的set方法来赋值；
3. Mybatis 在处理＄{}时， 就是把＄{}替换成变量的值。
4. 使用#{}可以有效的防止SQL 注入， 提高系统安全性．

# 当实体类中的属性名和表中的字段名不一样， 怎么办？

第1种：通过在查询的sql语句中定义字段名的别名，让字段名的别名和实体类的属性名一致。



```
<select id=" selectorder" parametertype=" int" resultetype="me.gad.domain.order" >
    select order_id id, order_no orderno ,order_price price form
    orders where order_id=#{id};
</select>
```

第2种：通过 来映射字段名和实体类属性名的一一对应的关系。



```
<select id ="getOrder" parameterType=" int" resultMap= "orderresultmap" >
    select * from orders where order_id=#{id}
</select>
<resultMap type=" me.gad.domain.order" id=" orderresultmap" >
    < ！-用id 属性来映射主键字段－ ＞
    <id property=" id" column=" order_id" >
    < ！-用result 属性来映射非主键字段， property 为实体类属性名，column为数据表中的属性－＞
    <result property = "orderno" column =" order_no" />
    <result property=" price" column=" order_price" />
</reslutMap>
```

# 通常一个Xml 映射文件， 都会写一个Dao 接口与之对应，请问， 这个Dao 接口的工作原理是什么? Dao 接口里的方法，参数不同时， 方法能重载吗？

全限名+接口的方法名（即id值）

方法不能重载，因为Mapper接口的工作原理是JDK动态代理，Mybatias运行时会使用jdk动态代理为mapper接口生成代理对象proxy，代理对象会拦截接口方法，转而去执行sql，所以不能重载。

# Mybatis 是如何将sql 执行结果封装为目标对象井返回的？都有哪些映射形式？

- 第一种是使用 标签，逐一定义数据库列名和对象属性名之间的映 射关系。
- 第二种是使用sql 列的别名功能，将列的别名书写为对象属性名。

有了列名与属性名的映射关系后， Mybatis通过反射创建对象，同时使用反射给 对象的属性逐一赋值并返回， 那找不到映射关系的属性使无法赋值的

# 在mapper 中如何传递多个参数？

第一种：

Dao层中的函数传入了多个参数，在对应的xml中， #{0}代表第一个参数，#{1}代表DAO层中的第二个参数，依次类推

第二种

使用@param注解

用@param（）给参数起一个名，在xml可以用#{}+这个起点名字来使用

第三章

使用Map集合作为参数来装载

# Mybatis 是否支持延迟加载？如果支持，它的实现原理是什么？

Mybatis 仅支待association 关联对象和collection关联组合对象的延迟加 载，association指的就是一对一，collection指的就是一对多。在Mybatis 配置文件中， 可以配置是否启用延迟加载lazyloadingEnabled =true | false.

# mybatis缓存

1、一级缓存：SqlSession 级别，默认开启，并且不能关闭。

操作数据库时需要创建 SqlSession 对象，在对象中有一个 HashMap 用于存储缓存数据，不同的SqlSession 之间缓存数据区域是互不影响的。

一级缓存的作用域是 SqlSession 范围的，当在同一个 SqlSession 中执行两次相同的 SQL 语句时，第一次执行完毕会将结果保存到缓存中，第二次查询时直接从缓存中获取。

需要注意的是，如果 SqlSession 执行了 DML 操作（insert、update、delete），MyBatis 必须将缓存清空以保证数据的准确性。

2、二级缓存：Mapper 级别，默认关闭，可以开启。

使用二级缓存时，多个 SqlSession 使⽤用同一个 Mapper 的 SQL 语句操作数据库，得到的数据会存在二级缓存区，同样是使用 HashMap 进行数据存储，相比较于一级缓存，二级缓存的范围更大，多个SqlSession 可以共用二级缓存，二级缓存是跨 SqlSession 的。

二级缓存是多个 SqlSession 共享的，其作用域是 Mapper 的同一个 namespace，不同的 SqlSession两次执行相同的 namespace 下的 SQL 语句句，参数也相等，则第一次执行成功之后会将数据保存到二级缓存中，第二次可直接从二级缓存中取出数据。

# 使用MyBatis 的mapper 接口调用时有哪些要求？

1 、Mapper 接口方法名和mapper.xml 中定义的每个sql 的id 相同，
2、Mapper 接口方法的输入参数类型和mapper.xml 中定义的每个sql 的 parameterType 的类型相同，
3 、Mapper 接口方法的输出参数类型和mapper.xml 中定义的每个sql 的 resultType 的类型相同，
4、Mapper.xml 文件中的namespace 即是mapper 接口的类路径。

# Mapper编写有哪几种方式？





第一种：接口实现类继承SqlSessionDaoSupport：使用此种方法需要编写mapper接口，mapper接口实现类、mapper.xml文件。



（1）在sqlMapConfig.xml中配置mapper.xml的位置



<mappers>



```
&lt;mapper resource=&quot;mapper.xml文件的地址&quot; /&gt;

&lt;mapper resource=&quot;mapper.xml文件的地址&quot; /&gt;
```



</mappers>



（2）定义mapper接口



（3）实现类集成SqlSessionDaoSupport



mapper方法中可以this.getSqlSession()进行数据增删改查。



（4）spring 配置



<bean id=" " class="mapper接口的实现">



```
&lt;property name=&quot;sqlSessionFactory&quot; ref=&quot;sqlSessionFactory&quot;&gt;&lt;/property&gt;
```



</bean>



第二种：使用org.mybatis.spring.mapper.MapperFactoryBean：



（1）在sqlMapConfig.xml中配置mapper.xml的位置，如果mapper.xml和mappre接口的名称相同且在同一个目录，这里可以不用配置



<mappers>



```
&lt;mapper resource=&quot;mapper.xml文件的地址&quot; /&gt;

&lt;mapper resource=&quot;mapper.xml文件的地址&quot; /&gt;
```



</mappers>



（2）定义mapper接口：



①mapper.xml中的namespace为mapper接口的地址



②mapper接口中的方法名和mapper.xml中的定义的statement的id保持一致



③Spring中定义



<bean id="" class="org.mybatis.spring.mapper.MapperFactoryBean">



```
&lt;property name=&quot;mapperInterface&quot;   value=&quot;mapper接口地址&quot; /&gt; 

&lt;property name=&quot;sqlSessionFactory&quot; ref=&quot;sqlSessionFactory&quot; /&gt; 
```



</bean>



第三种：使用mapper扫描器：



（1）mapper.xml文件编写：



mapper.xml中的namespace为mapper接口的地址；



mapper接口中的方法名和mapper.xml中的定义的statement的id保持一致；



如果将mapper.xml和mapper接口的名称保持一致则不用在sqlMapConfig.xml中进行配置。



（2）定义mapper接口：



注意mapper.xml的文件名和mapper的接口名称保持一致，且放在同一个目录



（3）配置mapper扫描器：



<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">



```
&lt;property name=&quot;basePackage&quot; value=&quot;mapper接口包地址&quot;&gt;&lt;/property&gt;

&lt;property name=&quot;sqlSessionFactoryBeanName&quot; value=&quot;sqlSessionFactory&quot;/&gt; 
```



</bean>



（4）使用扫描器后从spring容器中获取mapper的实现对象。