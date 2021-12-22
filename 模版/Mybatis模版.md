# 1、MybatisUitls

~~~ java
import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;

import java.io.IOException;
import java.io.InputStream;

//构建sqlSessionFactory,用它产生sqlSession
public class MybatisUtil {
    private static SqlSessionFactory sqlSessionFactory;
    static {
        try {
            //使用Mybatis第一步：获取sqlSessionFactory对象
            String resource = "mybatis-config.xml";
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    //既然有了 sqlSessionFactory，顾名思义，我们就可以从中获得 SqlSession 的实例了。
    //SqLSession完全包含了面数据库执行soL命令所需的所有方法。
    public static SqlSession getSqlSession(){
        //参数为true意味着以后所有事务不需要commit，会自动commit
        return sqlSessionFactory.openSession(true);
    }
}
~~~



# 2、MybatisConfig

~~~ java
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<!--configuration core file-->
<configuration>
    <properties resource="db.properties" >
        <property name="url" value="jdbc:mysql://localhost:3306/mybatisstudy?useSSL=true&amp;useUnicode=true&amp;characterEncoding=utf-8&amp;serverTimezone=UTC"/>
        <property name="driver" value="com.mysql.jdbc.Driver"/>
    </properties>

    <settings>
        <setting name="logImpl" value="STDOUT_LOGGING"/>
<!--        <setting name="logImpl" value="LOG4J"/>-->
    </settings>

    <typeAliases>
<!--        <typeAlias type="com.gu.pojo.User" alias="User" />-->
        <!--扫描实体类的包，默认别名就是类名的首字母小写-->
        <package name="com.gu.pojo"/>
    </typeAliases>

    <!--  环境配置，可以配置多个环境,default属性值表示默认环境  -->
    <environments default="development">
        <!-- 一个环境 -->
        <environment id="development">
            <!-- 事务管理 -->
            <transactionManager type="JDBC"/>
            <!-- 连接池 -->
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybatisstudy?useSSL=false&amp;useUnicode=true&amp;characterEncoding=utf-8&amp;serverTimezone=UTC"/>
                <property name="username" value="097"/>
                <property name="password" value="123456"/>
            </dataSource>
        </environment>

        <!-- 一个环境 -->
        <environment id="test">
            <!-- 事务管理 -->
            <transactionManager type="JDBC"/>
            <!-- 连接池 -->
            <dataSource type="POOLED">
                <property name="driver" value="${driver}"/>
                <property name="url" value="${url}"/>
                <property name="username" value="${username}"/>
                <property name="password" value="${password}"/>
            </dataSource>
        </environment>
    </environments>
    
    <mappers>
        <mapper class="com.gu.dao.UserMapper"/>
    </mappers>
</configuration>
~~~



# 3、MapperXML

~~~ xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.gu.dao.UserMapper">
    <select id="getUserList" resultType="com.gu.pojo.User">
        select * from user
    </select>
</mapper>
~~~

# 4、log4j日志

~~~ xml
    <dependencies>
        <!-- https://mvnrepository.com/artifact/log4j/log4j -->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>1.2.17</version>
        </dependency>
    </dependencies>
~~~

log4j.properties

~~~ pro
#将等级为DEBUG的日志信息输出到console和file这两个目的地，console和file的定义在下面的代码
log4j.rootLogger = DEBUG,console ,file

#控制台输出的相关设置
log4j.appender.console = org.apache.log4j.ConsoleAppender
log4j.appender.console.Target = System.out
log4j.appender.console.Threshold = DEBUG
log4j.appender.console.layout = org.apache.log4j.PatternLayout
log4j.appender.console.layout.ConversionPattern =  [%c]-%m%n

#文件输出的相关设置
log4j.appender.file = org.apache.log4j.RollingFileAppender
log4j.appender.file.File = ./log/kuang.log
log4j.appender.file.MaxFileSize = 10mb
log4j.appender.file.Threshold = DEBUG
log4j.appender.file.layout = org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern = [%p][%d{yy-MM-dd}][%c]%m%n

#日志输出级别
log4j.logger.org.mybatis=DEBUG
log4j.logger.java.sql=DEBUG
log4j.logger.java.sql.Statement=DEBUG
log4j.logger.java.sql.ResultSet=DEBUG
log4j.logger.java.sql.PreparedStatement=DEBUG
~~~

~~~ xml
    <settings>
        <setting name="logImpl" value="LOG4J"/>
    </settings>
~~~



# 5、解决资源过滤问题

~~~ xml
    <build>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
    </build>
~~~



