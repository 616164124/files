[TOC]







环境：jdk1.80_231

# 一、Springboot JPA中的关联查询









# 二、Mybatis







# 三、Rabbitmq

参考网址： https://blog.csdn.net/hellozpc/article/details/81436980 

[视频](<https://www.bilibili.com/video/av78225169?p=100>)

卸载需要注册表删除

## 3.1 工作模式

### 3.1.1 work queue（工作队列模式）

![](F:\hua\文件\files\jpg\20180805224950612.png)

work queue：两个消费端共同消费同一个队列中的消息，它的特点如下：

一个生产者将消息发给一个队列 多个消费者共同监听一个队列的消息

**消息不能被重复消费**

rabbit采用**轮询**的方式将消息平均发送给消费者

### 3.1.2  Publish / Subscribe ( 发布/订阅模式)





# 四、springboot

## 4.1 @RequestParam和@PathVariable的区别

 <font color=#0099ff > @RequestParam和@PathVariable  </font>

>  相同点与区别

 @RequestParam和@PathVariable都能够完成类似的功能——因为本质上，它们都是用户的输入，只不过输入的部分不同，一个在URL路径部分，另一个在参数部分。要访问一篇博客文章，这两种URL设计都是可以的：

- 通过@PathVariable，例如/blogs/1
- 通过@RequestParam，例如blogs?blogId=1

那么究竟应该选择哪一种呢？建议：

1、当URL指向的是某一具体业务资源（或资源列表），例如博客，用户时，使用@PathVariable

2、当URL需要对资源或者资源列表进行过滤，筛选时，用@RequestParam

例如我们会这样设计URL：

- /blogs/{blogId}
- /blogs?state=publish    而不是/blogs/state/publish来表示处于发布状态的博客文章

> 更多用法

 一旦我们在方法中定义了@RequestParam变量，如果访问的URL中不带有相应的参数，就会抛出异常——这是显然的，Spring尝试帮我们进行绑定，然而没有成功。但有的时候，参数确实不一定永远都存在，这时我们可以通过定义required属性：

```java
@RequestParam(value = "id", required = false)
```

当然，在参数不存在的情况下，可能希望变量有一个默认值：

```java
@RequestParam(value = "id", required = false, defaultValue = "0")
```

## 五、springbootAOP  

​	参考网站 https://www.bilibili.com/video/BV1KT4y1G7hs?from=search&seid=2723361983515545802

### 1、pom文件 dependencies 部分的内容

```xml
  <dependencies>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-web</artifactId>
            <version>5.3.4.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-aop</artifactId>
        </dependency>
      <!--热部署-->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<optional>true</optional>
		</dependency>

    </dependencies>
<!--打包-->
<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
				<configuration>
					<fork>true</fork>
				</configuration>
			</plugin>
		</plugins>
	</build>
```

### 2、五种常见的通知 5种Advice(通知)

​	前置通知：在我们执行目标方法之前运行（@before）

​	后置通知：	在我们执行目标方法运行结束之后，不管有没有异常（@after）

​	返回通知：在我们的目标方法正常返回值之后运行（@afterReturning）

​	异常通知：在我们的目标方法出现<font color=#ee11111>异常后运行</font>（@afterThrowing）

​	环绕通知：动态代理，需要手动执行joinPoint.procced（）（其实就是我们的目标方法执行之前相当于前置通		知，执行之后就相当于后置通知）

### 3、excution表达式

具体详情内容参考    [网址](https://blog.csdn.net/ABCD898989/article/details/50809321?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.channel_param)

```java
在使用spring框架配置AOP的时候，不管是通过XML配置文件还是注解的方式都需要定义pointcut"切入点"

例如定义切入点表达式 execution(* com.sample.service.impl..*.*(..))
execution()是最常用的切点函数，其语法如下所示：
 整个表达式可以分为五个部分：
 1、execution(): 表达式主体。

 2、第一个*号：表示返回类型，*号表示所有的类型。

 3、包名：表示需要拦截的包名，后面的两个句点表示当前包和当前包的所有子包，com.sample.service.impl包、子孙包下所有类的方法。

 4、第二个*号：表示类名，*号表示所有的类。

 5、*(..):最后这个星号表示方法名，*号表示所有的方法，后面括弧里面表示方法的参数，两个句点表示任何参数。
```





# springboot杂谈

通信无状态链接 http rest   弊端：<font color=#ee1111 >每请求占一个连接</font>

