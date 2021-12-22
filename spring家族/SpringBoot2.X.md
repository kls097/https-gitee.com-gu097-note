# 一、运行原理初探

- 注解：

    ![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-TpfYuOlH-1594913883183)(C:\Users\邓联庆\AppData\Roaming\Typora\typora-user-images\image-20200709105510753.png)]](https://gitee.com/gu097/note/raw/master/img/202110251936091.png)

    ```java
    //获取所有配置
    protected List<String> getCandidateConfigurations(AnnotationMetadata metadata, AnnotationAttributes attributes);
    ```
    
    获取候选配置：
    
    ```java
        protected List<String> getCandidateConfigurations(AnnotationMetadata metadata, AnnotationAttributes attributes) {
            List<String> configurations = SpringFactoriesLoader.loadFactoryNames(this.getSpringFactoriesLoaderFactoryClass(), this.getBeanClassLoader());
            Assert.notEmpty(configurations, "No auto configuration classes found in META-INF/spring.factories. If you are using a custom packaging, make sure that file is correct.");
            return configurations;
        }
    ```

# 二、JSR303数据校验及多环境切换

1. **配置文件加载位置**

    [外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-5Nr27xHV-1594913883189)(D:\我\MyBlog\狂神说Java SpringBoot.assets\image-20200709213144157.png)]

 **file : 文件路径，就是项目路径**

 [外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-MmY445bN-![1594913883192)(D:\我\MyBlog\狂神说Java SpringBoot.assets\image-20200709213352422.png)]](https://img-blog.csdnimg.cn/20200716233911191.png)

# 三、SpringBoot Web开发

**自动装配：**

SpringBoot到底帮我们配置了什么？我们能不能进行修改？能修改哪些东西？能不能扩展？

- xxxAutoConfiguration…向容器中自动配置组件
- xxxProperties：自动配置类，装配配置文件中自定义的一些内容

**要解决的问题：**

- 导入静态资源…

- 首页

- jsp, 模板引擎Thymeleaf

    thymeleaf依赖

- 装配扩展SpringMVC

- 增删改查

- 拦截器

- 国际化

# 四、员工管理系统

1. 首页配置
    1. 注意点，所有页面的静态资源都需要使用thymeleaf接管；（导入thymeleaf依赖）
    2. url: @{}
2. 页面国际化
    1. 我们需要配置i18n文件
    2. 我们如果需要在项目中进行按钮自动切换，我们需要自定义一个组件`LocaleResolver`
    3. 记得将自己写的组件配置到spring容器`@Bean`
    4. \#{}

# 五、整合MyBatis

**整合包**

**mybatis-spring-boot-starter**

1. 导入包

    ```xml
    <!--引入mybatis,这是Mybatis官方提供的适配SpringBoot的，而不是SpringBoot自己的-->
    <dependency>
        <groupId>org.mybatis.spring.boot</groupId>
        <artifactId>mybatis-spring-boot-starter</artifactId>
        <version>2.1.1</version>
    </dependency>
    ```
    
2. 配置yml文件

    **application.yml**

    ```yml
    # 配置spring自带的数据源
    spring:
      datasource:
        username: root
        password: root
        url: jdbc:mysql://localhost:3306/mybatis?userSSL=true&useUnicode=true&characterEncoding=UTF-8&serverTimezone=UTC
        driver-class-name: com.mysql.cj.jdbc.Driver
    
    # 整合mybatis
    mybatis:
      # 别名
      type-aliases-package: com.kuang.pojo
      # mapper文件位置
      mapper-locations: classpath:mybatis/mapper/*.xml
    ```
    
3. mybatis配置

    - User

        ```java
        @Data
        @AllArgsConstructor
        @NoArgsConstructor
        public class User {
            private int id;
            private String name;
            private String password;
        }
        ```
        
    - UserMapper接口
    
        ```java
        @Repository
        @Mapper
        public interface UserMapper {
            public User queryUserByName(String name);  
        }
        ```
        
    - UserMapper.xml配置文件

        ```xml
        <!--namespace=绑定一个指定的Dao/Mapper接口-->
        <mapper namespace="com.kuang.mapper.UserMapper">
            <select id="getUserList" resultType="com.kuang.pojo.User" parameterType="String">
            select * from USER where name = #{name}
          	</select>
        </mapper>
        ```
    
4. 编写sql

5. service层调用dao层

    - UserService 接口

        ```java
        public interface UserService {
            public User queryUserByName(String name);
        }
        ```
        
    - UserServiceImpl实现类
    
        ```java
        @Service
        public class UserServiceImpl implements UserService{
            @Autowired
            UserMapper mapper;
            public User queryUserByName(String name) {
                User user = mapper.queryUserByName(name);
                return user;
            }
        }
        ```
    
6. controller调用service层

    ```java
    @Autowired
    UserServiceImpl userService;
    public void mian(String args[]){
        User user = userService.queryUserByName("dog");
    }
    ```

# 六、SpringSecurity

1. 引入 Spring Security 模块

2. 编写 Spring Security 配置类

    参考官网：https://spring.io/projects/spring-security

3. 编写基础配置类

    - 定制请求的授权规则
    - 定义认证规则

    ```java
    //AOP : 拦截器
    @EnableWebSecurity
    public class SecurityConfig extends WebSecurityConfigurerAdapter {
    
        // 链式编程
        @Override
        //授权
        protected void configure(HttpSecurity http) throws Exception {
            //首页所有人可以访问，功能页只有对应有权限的人才能访问
            //请求授权的规则
            http.authorizeRequests()
                    .antMatchers("/").permitAll()
                    .antMatchers("/level1/**").hasRole("vip1")
                    .antMatchers("/level2/**").hasRole("vip2")
                    .antMatchers("/level3/**").hasRole("vip3");
    
            //没有权限默认会到登录页面,需要开启登录的页面
            http.formLogin()
                    .loginPage("/toLogin")
                    .usernameParameter("username")
                    .passwordParameter("password")
                    .loginProcessingUrl("/login");
    
            http.csrf().disable();//关闭csrf功能:跨站请求伪造,默认只能通过post方式提交logout请求
            // 开启注销功能
            http.logout().logoutSuccessUrl("/");
            //开启记住我功能
            http.rememberMe().rememberMeParameter("rememberme");
        }
    
        //认证
        @Override
        protected void configure(AuthenticationManagerBuilder auth) throws Exception {
       //在内存中定义，也可以在jdbc中去拿....
       //Spring security 5.0中新增了多种加密方式，也改变了密码的格式。
       //要想我们的项目还能够正常登陆，需要修改一下configure中的代码。我们要将前端传过来的密码进行某种方式加密
       //spring security 官方推荐的是使用bcrypt加密方式。
    
            auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
                    .withUser("kuangshen").password(new BCryptPasswordEncoder().encode("123456")).roles("vip2","vip3")
                    .and()
                    .withUser("admin").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2","vip3")
                    .and()
                    .withUser("guest").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1");
        }
    }
    ```

# 七、Shiro

- Subject 用户
- SecurityManager 管理用户
- Realm 连接数据
    ![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251938014.png)
    **简单实验：**

1. 导入依赖

    ```xml
    <dependency>
        <groupId>org.apache.shiro</groupId>
        <artifactId>shiro-spring</artifactId>
        <version>1.5.3</version>
    </dependency>
    ```
    
2. 编写Shiro配置类

    ```java
    @Configuration
    public class ShrioConfig {
        //ShiroFilterFactoryBean : Step3
        @Bean
        public ShiroFilterFactoryBean getShrioFilterFactoryBean(@Qualifier("securityManager") DefaultWebSecurityManager defaultWebSecurityManager){
            ShiroFilterFactoryBean bean = new ShiroFilterFactoryBean();
            //设置安全管理器
            bean.setSecurityManager(defaultWebSecurityManager);
            return bean;
        }
        
        //DefaultWebSecurityManager : Step2
        @Bean("securityManager")
        public DefaultWebSecurityManager getDefaultWebSecurityManager(@Qualifier("userRealm") UserRealm userRealm){
            DefaultWebSecurityManager securityManager = new DefaultWebSecurityManager();
            //关联userRealm
            securityManager.setRealm(userRealm);
            return securityManager;
        }
        
        //创建 realm 对象, 需要自定义类：Step1
        @Bean
        public UserRealm userRealm(){
            return new UserRealm();
        }
    }
    ```
    
3. 自定义UserRealm

    ```java
    //自定义的 UserRealm
    public class UserRealm extends AuthorizingRealm {
    
        //授权
        @Override
        protected AuthorizationInfo doGetAuthorizationInfo(PrincipalCollection principalCollection) {
            return null;
        }
    
        //认证
        @Override
        protected AuthenticationInfo doGetAuthenticationInfo(AuthenticationToken authenticationToken) throws AuthenticationException {
            return null;
        }
    }
    ```

**一个小Demo:**

1. 导入依赖

    - springboot-mybatis整合
    - shiro-thymelea整合

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <parent>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-parent</artifactId>
            <version>2.3.1.RELEASE</version>
            <relativePath/> <!-- lookup parent from repository -->
        </parent>
        <groupId>com.kuang</groupId>
        <artifactId>shiro-springboot</artifactId>
        <version>0.0.1-SNAPSHOT</version>
        <name>shiro-springboot</name>
        <description>Demo project for Spring Boot</description>
    
        <properties>
            <java.version>1.8</java.version>
        </properties>
    
        <dependencies>
            <!--shiro-thymeleaf整合-->
            <dependency>
                <groupId>com.github.theborakompanioni</groupId>
                <artifactId>thymeleaf-extras-shiro</artifactId>
                <version>2.0.0</version>
            </dependency>
    
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>8.0.20</version>
            </dependency>
            <!-- https://mvnrepository.com/artifact/log4j/log4j -->
            <dependency>
                <groupId>log4j</groupId>
                <artifactId>log4j</artifactId>
                <version>1.2.17</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba</groupId>
                <artifactId>druid</artifactId>
                <version>1.1.22</version>
            </dependency>
            <!--引入mybatis,这是Mybatis官方提供的适配SpringBoot的，而不是SpringBoot自己的-->
            <dependency>
                <groupId>org.mybatis.spring.boot</groupId>
                <artifactId>mybatis-spring-boot-starter</artifactId>
                <version>2.1.1</version>
            </dependency>
            <dependency>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
                <version>1.18.12</version>
            </dependency>
            <dependency>
                <groupId>org.apache.shiro</groupId>
                <artifactId>shiro-spring</artifactId>
                <version>1.5.3</version>
            </dependency>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-thymeleaf</artifactId>
            </dependency>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-web</artifactId>
            </dependency>
    
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-test</artifactId>
                <scope>test</scope>
                <exclusions>
                    <exclusion>
                        <groupId>org.junit.vintage</groupId>
                        <artifactId>junit-vintage-engine</artifactId>
                    </exclusion>
                </exclusions>
            </dependency>
        </dependencies>
    
        <build>
            <plugins>
                <plugin>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-maven-plugin</artifactId>
                </plugin>
            </plugins>
        </build>
    
    </project>
    ```
    
2. 整合MyBatis

    - 编写实体类
    - 编写mapper接口、mapper.xml、application.yml配置mybatis（别名，mapper.xml文件位置)
    - 编写service接口，serviceImpl类
        ![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251938730.png)

3. 编写Shiro配置类

    ```java
    @Configuration
    public class ShrioConfig {
    
        //ShiroFilterFactoryBean : Step3
        @Bean
        public ShiroFilterFactoryBean getShrioFilterFactoryBean(@Qualifier("securityManager") DefaultWebSecurityManager defaultWebSecurityManager){
            ShiroFilterFactoryBean bean = new ShiroFilterFactoryBean();
            //设置安全管理器
            bean.setSecurityManager(defaultWebSecurityManager);
    
            //添加shiro的内置过滤器
            /*
                anno: 无需认证就可以访问
                authc: 必须认证了才可以访问
                user: 必须拥有 记住我 功能才能用
                perms: 拥有对某个资源的权限才能访问
                role: 拥有某个角色权限才能访问
            */
    
            Map<String, String> filterMap = new LinkedHashMap<>();
    
            //用户授权,正常情况下没有授权会跳转到授权页面
            filterMap.put("/user/add","perms[user:add]");
            filterMap.put("/user/update","perms[user:update]");
    
            //拦截
            //filterMap.put("/user/add","authc");
            //filterMap.put("/user/update","authc");
            filterMap.put("/user/*","authc");
    
            //设置登录请求
            bean.setLoginUrl("/toLogin");
            //设置未授权页面
            bean.setUnauthorizedUrl("/noauth");
            bean.setFilterChainDefinitionMap(filterMap);
            return bean;
        }
    
        //DefaultWebSecurityManager : Step2
        @Bean("securityManager")
        public DefaultWebSecurityManager getDefaultWebSecurityManager(@Qualifier("userRealm") UserRealm userRealm){
            DefaultWebSecurityManager securityManager = new DefaultWebSecurityManager();
            //关联userRealm
            securityManager.setRealm(userRealm);
            return securityManager;
        }
    
        //创建 realm 对象, 需要自定义类：Step1
        @Bean
        public UserRealm userRealm(){
            return new UserRealm();
        }
    
        //整合 ShiroDialect:用来整合shiro thymeleaf
        @Bean
        public ShiroDialect getShiroDialect(){
            return new ShiroDialect();
        }
    }
    1234567891011121314151617181920212223242526272829303132333435363738394041424344454647484950515253545556575859
    ```

4. 自定义UserRealm

    ```java
    //自定义的 UserRealm
    public class UserRealm extends AuthorizingRealm {
    
        @Autowired
        UserServiceImpl userService;
    
        //授权
        @Override
        protected AuthorizationInfo doGetAuthorizationInfo(PrincipalCollection principalCollection) {
            System.out.println("执行了 => doGetAuthorizationInfo");
    
            SimpleAuthorizationInfo info = new SimpleAuthorizationInfo();
            // 拿到当前登录的这个对象
            Subject subject = SecurityUtils.getSubject();
            // 拿到User对象
            User currentUser = (User) subject.getPrincipal();
            // 设置当前用户的权限
            System.out.println(currentUser.getName() + "的权限为 " + currentUser.getPerms());
            info.addStringPermission(currentUser.getPerms());
    
            return info;
        }
    
        //认证
        @Override
        protected AuthenticationInfo doGetAuthenticationInfo(AuthenticationToken authenticationToken) throws AuthenticationException {
            System.out.println("执行了 => 认证AuthenticationToken");
    
            UsernamePasswordToken userToken = (UsernamePasswordToken) authenticationToken;
            //连接真实的数据库
            User user = userService.queryUserByName(userToken.getUsername());
            if(user == null){
                //没有这个人
                return null; //抛出异常 UnknownAccountException
            }
    
            // 登录成功 将用户信息存入session
            Subject currentSubject = SecurityUtils.getSubject();
            Session session = currentSubject.getSession();
            session.setAttribute("loginUser",user.getName());
    
            // 密码认证，shiro做
            return new SimpleAuthenticationInfo(user,user.getPassword(),"");
        }
    }
    123456789101112131415161718192021222324252627282930313233343536373839404142434445
    ```

# 八、Swagger

学习目标：

- 了解Swagger的作用和概念
- 了解前后端分离
- 在SpringBoot中集成Swagger

## 一、 Swagger简介

**前后端分离时代：**

- 后端：后端控制层，服务层，数据访问层
- 前端：前端控制层，视图层

**Swagger :**

- 号称世界上最流行的API框架；
- RestFul Api文档在线自动生成工具 => Api文档与Api定义同步更新
- 直接运行，可以在线测试API接口
- 支持多种语言：（Java , Php…）

在项目中使用Swagger需要Springbox

- swagger2
- ui

## 二、SpringBoot集成Swagger

1. 新建一个SpringBoot - web 工程

2. 导入相关依赖

    ```xml
    <!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger2 -->
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger2</artifactId>
        <version>2.9.2</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger-ui</artifactId>
        <version>2.9.2</version>
    </dependency>
    
    12345678910111213
    ```

3. 编写一个Hello工程

4. 配置Swagger ==> Config

    ```java
    @Configuration
    @EnableSwagger2 //开启Swagger
    public class SwaggerConfig {
      
    }
    12345
    ```

5. 测试运行：http://localhost:8080/swagger-ui.html

## 三、 **配置Swagger**信息

```java
@Configuration
@EnableSwagger2 //开启Swagger
public class SwaggerConfig {
    //配置了Swagger 的Docket的bean实例
    @Bean
    public Docket docket(){
        return new Docket(DocumentationType.SWAGGER_2).apiInfo(apiInfo());
    }
    
    //配置Swagger信息=apiInfo
    public ApiInfo apiInfo(){
        //作者信息
        Contact contact = new Contact("Daniel","https://www.baidu.com","denglianqing@qq.com");
        return new ApiInfo("Dainel的SwaggerAPI文档",
                "天道酬勤",
                "v1.0",
                "urn:tos",
                contact, "Apache 2.0",
                "http://www.apache.org/licenses/LICENSE-2.0",
                new ArrayList());
    }
}
12345678910111213141516171819202122
```

## 四、 Swagger配置扫描接口

**Docket.select（）**

```java
//配置了Swagger 的Docket的bean实例
@Bean
public Docket docket(){
    return new Docket(DocumentationType.SWAGGER_2).apiInfo(apiInfo())
        .select()
        //RequestHandlerSelectors,配置要扫描接口的方式
        //basePackage，指定要扫描的包
        //any(): 扫描全部
        .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
        .paths(PathSelectors.ant("/kuang/**"))
        .build();
}
123456789101112
```

> 题目：我只希望我的Swagger在生产环境中使用，在发布的时候不使用
>
> - 判断是不是生产环境 flag = false
> - 注入enable （flag）

```java
//配置了Swagger 的Docket的bean实例
@Bean
public Docket docket(Environment environment){

    //设置要显示的Swagger环境
    Profiles profiles = Profiles.of("dev","test");
    //通过  environment.acceptsProfiles 判断是否处在自己设定的环境中
    boolean flag = environment.acceptsProfiles(profiles);
    ...
}
12345678910
```

![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-FZX3xgNm-1594913883200)(D:\我\MyBlog\狂神说 SpringBoot.assets\image-20200715113453865.png)]](https://gitee.com/gu097/note/raw/master/img/202110251938013.png)

**配置API文档的分组**

```java
.groupName("狂神")
1
```

如何配置多个分组；多个Docket实例即可
![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251938877.png)

## 五、 接口注释

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251938121.png)
**总结：**

1. 我们可以通过Swagger给一些比较难理解的属性或者接口，增加注释信息；
2. 接口文档实时更新
3. 可以在线测试

Swagger是一个优秀的工具，几乎所有的大公司都有使用它

【注意点】在正式发布的时候，关闭Swagger！！出于安全考虑，而且节省运行的内存。

# 九、任务

## 一、异步任务

1. 给要实现异步任务加上注解 **@Async**

    ```java
    @Service
    public class AsyncService {
        @Async
        public void hello(){
            try {
                Thread.sleep(3000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("数据正在处理...");
        }
    }
    ```
    
2. 在main方法开启异步功能 **@EnableAsync**

    ```java
    @EnableAsync // 开启异步注解功能
    @SpringBootApplication
    public class Springboot09TaskApplication {
        public static void main(String[] args) {
            SpringApplication.run(Springboot09TaskApplication.class, args);
        }
    }
    ```

## 二、邮件任务

1. 导入依赖

    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-mail</artifactId>
    </dependency>
    ```
    
2. 配置邮箱和密码

    ```properties
    spring.mail.username=514906666@qq.com
    spring.mail.password=xxyyzzhhll
    spring.mail.host=smtp.qq.com
    # 开启加密验证
    spring.mail.properties.mail.smtp.ssl.enable=true
    ```
    
3. 测试发送邮件(组合邮件，带附件)

    ```java
    @SpringBootTest
    class Springboot09TaskApplicationTests {
    
        @Autowired
        JavaMailSenderImpl mailSender;
    
        @Test
        void contextLoads2() throws MessagingException {
    
            //一个复杂的邮件
            MimeMessage mimeMessage = mailSender.createMimeMessage();
            //组装
            MimeMessageHelper helper = new MimeMessageHelper(mimeMessage, true);
            //正文
            helper.setSubject("Test");
            helper.setText("<h2 style='color:red'> 这是一封测试邮件 </h2>",true);
            //附件
            helper.addAttachment("data1",new File("D:\\testdata\\2017-01-01.xls"));
    
            helper.setTo("dishifu@126.com");
            helper.setFrom("514906666@qq.com");
    
            mailSender.send(mimeMessage);
        }
    ```

## 三、定时任务

> 1. TaskScheduler 任务调度者
> 2. TaskExecutor 任务执行者
> 3. **@EnableScheduling** 开启定时功能的注解
> 4. **@Scheduled** 什么时候执行
> 5. **Cron表达式**

1. 编写定时服务

    ```java
    @Service
    public class ScheduledService {
    
        //在一个特定的时间执行这个方法
    
        //cron 表达式
        //秒 分 时 日 月 周几
    
        /*
            30 17 17 * * ?  每天10点15分30 执行一次
            30 0/5 10,18 * * ?  每天10点和18点，每隔五分钟执行一次
        */
    
        @Scheduled(cron = "30 17 17 * * ?")
        public void Hello(){
            System.out.println("hello,被执行了!");
        }
    
    }
    ```
    
2. 在启动类开启定时功能

    ```java
    @EnableAsync // 开启异步注解功能
    @EnableScheduling //开启定时功能的注解
    @SpringBootApplication
    public class Springboot09TaskApplication {
        public static void main(String[] args) {
            SpringApplication.run(Springboot09TaskApplication.class, args);
        }
    }
    ```

# 十、整合Redis

**单独整理**

# 十一、分布式Dubbo + Zookeeper

zookeeper ：注册中心

dubbo-admin : 监控管理后台，查我们注册了哪些服务，哪些服务被消费了

Dubbo：jar包

步骤：

前提：zookeeper服务已启动

1. 提供者提供服务

    - 导入依赖

    - 配置注册中心的地址，以及服务发现名，和要扫描的包

        ![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-zrVrmA8F-1594913883205)(D:\我\MyBlog\狂神说 SpringBoot.assets\image-20200716230709998.png)]](https://gitee.com/gu097/note/raw/master/img/202110251937888.png)

    - 在想要被注册的服务上面，再增加一个注解**@Service**（dubbo包下的）

2. 消费者如何消费

    - 导入依赖
    - 配置注册中心的地址，配置自己的服务名
        ![[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-ACONokw7-1594913883207)(D:\我\MyBlog\狂神说 SpringBoot.assets\image-20200716230419673.png)]](https://gitee.com/gu097/note/raw/master/img/202110251937531.png)
    - 从远程注入服务 **@Reference**

**微服务架构存在的问题:**

**分布式架构会遇到的四个核心问题**

1. 这么多服务，客户端该如何去访问
2. 这么多服务，服务之间如何进行通信
3. 这么多服务，如何管理
4. 服务挂了，该怎么办

==》 解决方案：

 SpringCloud，是一套生态，就是用来解决以上分布式架构的4个问题。

 想使用SpringCloud，必须掌握SpringBoot，因为SpringCloud是基于SpringBoot的

```
1. API网关，服务路由
2. HTTP，RPC框架，异步调用
3. 服务注册与发现，高可用
4. 熔断机制，服务降级
```