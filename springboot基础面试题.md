# springboot基础面试题

##  ![image-20210314033937734](C:%5C2file%5Cfiles%5Cassets%5Cimage-20210314033937734.png)



![image-20210314034804433](C:%5C2file%5Cfiles%5Cassets%5Cimage-20210314034804433.png)



![image-20210314035447352](C:%5C2file%5Cfiles%5Cassets%5Cimage-20210314035447352.png)



![image-20210314040812644](assets/image-20210314040812644.png)





## spring对bean的管理也是bean的生命周期

![img](assets/20190512223750452.png)

先调用构造函数进行实例化，然后填充属性，再接着进行其他附加操作和初始化，正是这样的生命周期，才有了Spring的解决循环依赖，这样的解决机制是根据Spring框架内定义的三级缓存来实现的，也就是说：三级缓存解决了Bean之间的循环依赖。



netty面试题

![image-20210315023035380](assets/image-20210315023035380.png)