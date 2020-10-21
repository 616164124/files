[TOC]







环境：

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
- /blogs?state=publish而不是/blogs/state/publish来表示处于发布状态的博客文章

> 更多用法

 一旦我们在方法中定义了@RequestParam变量，如果访问的URL中不带有相应的参数，就会抛出异常——这是显然的，Spring尝试帮我们进行绑定，然而没有成功。但有的时候，参数确实不一定永远都存在，这时我们可以通过定义required属性：

```java
@RequestParam(value = "id", required = false)
```

当然，在参数不存在的情况下，可能希望变量有一个默认值：

```java
@RequestParam(value = "id", required = false, defaultValue = "0")
```

## springboot杂谈

通信无状态链接 http rest   弊端：<font color=#ee1111 >每请求占一个连接</font>

