

# **java基础**

1、一个java文件只能有一个public，可以有多个类（不包括内部类）

2、&&和& 两者都是逻辑与的运算符，&&具有短路的功能，&可以用作位运算符 例如int a = 2&3;结果为2；int a = 2&1；结果为0；

3、值传递与引用传递 ：（java只有值传递）

​	(1)值传递传的是值的副本，副本的改变不会影响到原变量；

​	(2)引用传递就是将一个堆内存空间的使用权交给多个栈内存空间，每个栈内存空间都可以对堆内存空间进行修改

<font color=#ee11111>对象的引用存放在栈内存中，对象实例在堆内存中</font>

java方法参数的使用情况：

a、一个方法不能修改一个基本数据类型的参数（即布尔型和数值型）

b、一个方法可以改变一个对象参数的状态

c、一个方法不能让对象参数引用一个新的对象

​	

4、java中跳出当前多重嵌套循环？

第一种：在最外层循环语句前定义一个标号，循环体内任意位置都可以使用带有标号的break语句跳出外层循环，结束整个循环。缺点若代码片段太长，不易读；

第二种：使用boolean变量做flag，作为外层循环体结束的条件，赋予变量带有业务意义的名字。

​						

```java
 	 
第二种方法
	System.out.println("MainClass1 Start...");
        int arr[][] = { { 1, 2, 3 }, { 4, 5, 6, 7 }, { 9 } };
        boolean found = false;

        for (int i = 0; i < arr.length && !found; i++) {
            for (int j = 0; j < arr[i].length; j++) {
                System.out.println("i=" + i + ",j=" + j);
                if (arr[i][j] == 5) {
                    found = true;
                    break;
                }
            }
        }
        System.out.println("End.");
```

5、访问修饰符的区别

  		访问权限   类   包  子类  其他包

  　　　public     ∨   ∨     ∨      ∨          （对任何人都是可用的）

   　　   protect    ∨   ∨    ∨      ×　　　 （继承的类可以访问以及和private一样的权限）

   　　   default    ∨   ∨    ×       ×　　　 （包访问权限，即在整个包内均可被访问）

   　　    private    ∨   ×    ×       ×　　　 （除类型创建者和类型的内部方法之外的任何人都不能访问的元素）

6、switch（exp）中的exp包含 byte，short，char，int , Enum，String，Character，Byte，Short，Integer ；long类型可以写但是执行会报错。

7、char类型是用来保存Unicode编码的，其中Unicode编码包含汉字，char类型可以保存汉字，但是必须保证汉字在Unicode编码里的，Unicode编码占用两个字节，char也是

8、最有效的2乘以8等于16怎么写？   2<<3;意思为将2转换为2进制，想左移3位；5<<3 ;

​			5<<3   相当于 5*2^3 

​			4>>1 相当于 4 / 2

​			4>>2 相当于  4/ 4							

9、final  

​	（1）修饰类，当用final去修饰一个类的时候，表示这个类不能被继承。类中的成员方法都会被隐式的指定为final方法.

​      (2)修饰方法，父类中有final修饰的方法，那么子类不能去重写，

​	（3）修饰成员变量，a、初始化，b、直接赋值或者在构造方法中赋值，c、若为基本数据类型，则这个变量的值不能改变。d、如果修饰的成员变量是一个引用类型，则是说这个引用的地址的值不能修改，但是这个引用所指向的对象里面的内容还是可以改变的

10、==和equals区别：　1）对于==，如果作用于基本数据类型的变量，则直接比较其存储的 “值”是否相等；

　　　				　如果作用于引用类型的变量，则比较的是所指向的对象的地址

　　									2）对于equals方法，注意：equals方法不能作用于基本数据类型的变量

　　　　				如果没有对equals方法进行重写，则比较的是引用类型的变量所指向的对象的地址；

　　　　				诸如String、Date等类对equals方法进行了重写的话，比较的是所指向的对象的内容。

11、静态变量与实例变量区别?  

​	(1)都是独立于方法外的变量，静态变量时用static修饰的，

​	(2）实例变量其中的实例变量才会被分配空间，才能使用这个实例变量，静态变量只要程序加载了类的字节码，不用创建任何实例对象，静态变量就会被分配空间，静态变量就可以被使用了；

12、是否可以从一个static方法内部发出对非static方法的调用？**不可以**  static方法调用时不用创建对象，而非static方法要与对象关联在一起，必须创建一个对象后，才能进行方法的调用

13、Math.round()   x轴向右取值；floor 向左取值；ceil向右取值。

**14、hashcode方法 **

15、构造器Constructor不能被继承，即不能重写 ，但可以重载；

**16、  56~62**？？？？？？

17、StringBuffer和StringBuilder区别  

​	  两个类表示内容可以被修改的字符串，

​	（1）StringBuffer 线程安全运行效率慢使用于多线程 

​	（2）StringBuilder 线程不安全运行效率快使用于单线程

18、final，finally，finalize()的区别

​	a、final 声明属性，方法和类，表示属性不可改变，方法不可覆盖，类不可继承

​	b、finally是异常处理语句结构的一部分，表示总是执行

​	c、finalize()是Object的protected方法，子类可以覆盖该方法以实现资源清理工作，GC在回收对象之前调用该方法

19、异常65

20、Math.round(11.5)   为  12    Math.round(-11.5)  为   11

21、float f = 3.2  不正确 精度缺失

22、final，finally，finalize的区别：

![1603563410385](assets/1603563410385.png)



23、一个类FATHER被其他类SON继承

```java
/**
 * projectName: JUC   
 * fileName: FatherAndSon.java  
 * packageName: Interview   
 * copyright(c) 2017-2020 xxx公司  
 */
package Interview;

/**
 * @version: V1.0
 * @author: mikael
 * @className: FatherAndSon
 * @packageName: Interview
 * @description:构造方法 在	生成类的对象是自动执行，无需调用
 **/
public class FatherAndSon {
  public static void main(String[] args) {
      Son son = new Son();
  }
}

class Father{
    private int age;
    public Father() {
    System.out.println("father Father()");
    }

   public Father(int age) {
    System.out.println("father Father(int age)");
        this.age = age;
    }
}

class Son extends Father{
    private int age;
    public Son() {
    System.out.println("son Son()");
    }

   public Son(int age) {
    System.out.println("Son son(int age)");
        this.age = age;
    }

    public Son(int age, int age1) {
        super(age);     //没有这个行怎会报错
        this.age = age1;
    }
}
```





error与exception的区别

![1603619101976](assets/1603619101976.png)

### Java--getClass()和.Class的区别

------springboot中测试@Test 中，必须用的 . class形式

 getClass方法，有多态能力，运行时可以返回子类的类型信息，

 .class是没有多态的，是静态解析的，编译时可以确定类型信息。



## 强软弱虚

强： object o=new object（）

软：内存不够时，gc

弱：没有被引用就gc掉了   threadlocal 中的 map

虚：

## 抽象类、接口 、普通类的区别

1、抽象类就是用来被继承了，所以<font color=#ee1111 >不能用final修饰 </font> 。

2、抽象类中不一定包含抽象方法

3、有抽象方法一定是抽象类

a、接口里面所有的方法都是public，抽象类可以有private，protected

b、类可以实现多个接口，只能继承一个类

壹、普通类可以直接实例化，抽象类不能直接实例化

贰、普通类不能包含抽象方法，抽象类可以有抽象方法F

抽象类就是让人拿来继承的，所以不能被<font color=#ee11111>final</font>修饰

# 多线程

20、stop（）和suspend（）为何不推荐使用

​	a、stop（）不安全。会解除有线程获取的所有锁定，而且在对象处于一种不连贯的状态，其他线程能检查和修改对象。

​	b、suspend（）容易发生死锁。调用suspend方法的时候，目标线程会停下，但却依然持有之前获得的锁定，此时其他线程都不能访问锁定的资源，除非被“挂起”的线程恢复运行。对于任何线程来说，如果他们想恢复目标线程，同事又试图使用任何一个锁定的资源，就好造成死锁。更改的方法，在自己的线程类中置入一个标志，指出线程应该活动还是挂起，若挂起则使线程用wait（）进入等待状态，若恢复，则用一个notify（）重写启动线程。

21、sleep（）和wait()区别

​		sleep()方法，我们首先要知道该方法是属于Thread类中的。而wait()方法，则是属于Object类中的。

​		sleep()方法导致了程序暂停执行指定的时间，让出cpu该其他线程，但是他的监控状态依然保持者，当指定的时间到了又会自动恢复运行状态。

​		在调用sleep()方法的过程中，线程不会释放对象锁（占用对象）。

​		而当调用wait()方法的时候，线程会放弃对象锁（释放对象），进入等待此对象的等待锁定池，只有针对此对象调用notify()方法后本线程才进入对象锁定池准备

​		获取对象锁进入运行状态。

22、同步与异步的不同

​	同步 ： 共享数据的

​	异步：调用一个方法时，不想等待方法执行完时

23、当一个线程进入一个对象的synchronize方法后，其他线程是否可以进入此对象的其他方法？？？？       synchronize时修饰符

​		a、如果其他方法前是否加了synchronize，如果没有，则可以

​		b、如果这个方法内部调用了 wait()方法，则可以进入其他synchronize方法。

​		c、如果其他方法都加了synchronize，并且内部没有调用wait（）,则不能

​		d、如果其他方法是static，他用的同步锁是当前类的字节码，与非静态的方法不能同步

25、synchronize与lock的异同

​		相同点：Lock能完成synchronize所实现的所有的功能

​		不同点：Lock比synchronize更精确的线程语义和性能

​				synchronize会自动释放锁，而lock必须手工释放，finally中释放，且Lock中的tryLock方法可以分阻塞方式去拿锁：如果线程使用tryLock()不能获取锁，tryLock()会立即返回，它不会将线程置入休眠。tryLock()方法返回一个布尔值，true表示线程获取了锁，false表示没有获取锁。

26、线程的几种状态？

[参考网址](https://blog.csdn.net/pange1991/article/details/53860651?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.channel_param)

```java
1. 初始(NEW)：新创建了一个线程对象，但还没有调用start()方法。
2. 运行(RUNNABLE)：Java线程中将就绪（ready）和运行中（running）两种状态笼统的称为“运行”。
线程对象创建后，其他线程(比如main线程）调用了该对象的start()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获取CPU的使用权，此时处于就绪状态（ready）。就绪状态的线程在获得CPU时间片后变为运行中状态（running）。
3. 阻塞(BLOCKED)：表示线程阻塞于锁。
4. 等待(WAITING)：进入该状态的线程需要等待其他线程做出一些特定动作（通知或中断）。
5. 超时等待(TIMED_WAITING)：该状态不同于WAITING，它可以在指定的时间后自行返回。
6. 终止(TERMINATED)：表示该线程已经执行完毕。
```

 这6种状态定义在Thread类的State枚举中，可查看源码进行一一对应。 



27、run() 和start（）区别

​	run()方法当作普通方法的方式调用。程序还是要顺序执行，要等待 run 方法体执行完毕后，才可继续执行下面的代码

​        start() 方法来启动线程，真正实现了多线程运行。这时无需等待 run 方法体代码执行完毕，可以直接继续执行下面的代码

28、线程调度和线程控制

​	**线程调度（）优先级** ：线程优先级的范围是1～10，默认的优先级是5。10极最高。“高优先级线程”被分配CPU的概率高于“低优先级线程”。

​	**线程控制**： sleep（）线程休眠

​			   join（）线程加入

​			  yield（）线程礼让

​			setDaemon（）线程守护

​	中断线程 ： stop（），interrupt（）首选后者

29、线程饿死，什么是活锁

-  死锁：是指两个或两个以上的进程（或线程）在执行过程中，因争夺资源而造成的一种相互等待的现象，若无外力作用，他们将无法推进下去；

- 活锁：是指两个线程优先级相同，都礼让不走，就这样一直僵持下去；

- 饿死：在单线程情况下，A、B两个线程，A先执行；A在执行过程中，C线程来了，B让C先执行；C在执行过程中，D线程来了，B也让D先执行，就这样B一直都是等待状态。

- 竞态条件：多个线程竞争同一个变量，导致数据的不正确性，线程的访问顺序是不可控的，会影响最终的结果。

  产生死锁的必要条件：

  1、互斥使用（资源独占）

  　　一个资源每次只能给一个进程使用（比如写操作）

  2、占有且等待：

  　　进程在申请新的资源的同时，保持对原有资源的占有

  3、不可抢占：

  　　资源申请者不能强行从资源占有者手动夺取资源，资源只能由占有者自愿释放

  4、循环等待：

  　　A等待B占有的资源，B等待C占有的资源，C等待D占有的资源，..........N等待A的资源，形成一个线程等待回路

30、多线程的忙循环？

​	循环就是程序员用循环让一个线程等待，不像传统方法wait(), sleep() 或 yield() 它们都放弃了CPU控制，而忙循环不会放弃CPU，它就是在运行一个空循环。这么做的目的是为了保留CPU缓存，在多核系统中，一个等待线程醒来的时候可 能会在另一个内核运行，这样会重建缓存。为了避免重建缓存和减少等待重建的时间就可以使用它了。

31、volatile 保证所修饰的变量在多线程中的可见性且这个变量不会存在复本，直接从内存中读取

1、start（）执行即返回，不等run中全部的代码块执行结束。

```
    public static void main(String[] args) {

​        new Thread("thread-one"){
​            public void run(){

​                for (int i = 0; i < 1000000; i++) {
​                    if (i == 99) {
​                        System.out.println("i==99"); 第二句
​                    }

​                }

​                System.out.println("thread-one：结束"); 第三句

​            }
​        }.start();

​        System.out.println("thread-one：结束22222");  第一句

​    }
```

2、线程生命周期   

new ---》》 runnable ---    》》 running  ---》》      block -----------》》                         termate

​                  	 就绪                  	   调用cpu执行    		   锁（sleep，wait ）           		   死亡

3、当你执行一个线程的start方法时，此时至少有两个线程，一个是调用你的线程，另一个是执行run方法的线程

4、阻塞队列（）

![image-20201105143709533](assets/image-20201105143709533.png)

5、线程池

# **集合**

32、ArrayList和vector的区别

​	两个类都实现了List接口（List接口继承了Collection接口），他们都是有序集合（按添加的顺序），		

（1）：Vector是线程安全的，源码中有很多的synchronized可以看出，而ArrayList不是。导致Vector效率无法和ArrayList相比；

（2）：ArrayList和Vector都采用线性连续存储空间，当存储空间不足的时候，ArrayList默认增加为原来的50%，Vector默认增加为原来的一倍；

（3）：ArrayList与Vector都可以设置初始的空间大小，Vector还可以设置增长的空间大小，而ArrayList没有提供设置增长空间的方法。

33、ArrayList和vector LinkedList存储性能和特性

​	ArrayList 和Vector他们底层的实现都是一样的，都是使用数组方式存储数据，此数组元素数大于实际存储的数据以便增加和插入元素，

​	它们都允许直接按序号索引元素，但是插入元素要涉及数组元素移动等内存操作，所以索引数据快而插入数据慢。

​      Vector中的方法由于添加了synchronized修饰，因此Vector是线程安全的容器，但性能上较ArrayList差。

​      LinkedList使用双向链表实现存储（将内存中零散的内存单元通过附加的引用关联起来，形成一个可以按序号索引的线性结构，这种链式存储方式与数组的连续存储方式相比，内存的利用率更高），

按序号索引数据需要进行前向或后向遍历，但是插入数据时只需要记录本项的前后项即可，所以插入速度较快。            

​	**ArrayList 在查找时速度快，LinkedList在插入与删除时更好**

34、hashmap的数据结构一个数组和链表的结合体 也称为 链表散列

35、hashmap的工作原理   ---------**hashCode是用来在散列存储结构中确定对象的存储地址的**

1. 利用key的hashCode重新计算出当前对象的元素在数组中的下标
2. 存储时，如果出现hash值相同的key，此时有两种情况。(1)如果key相同，则覆盖原始值；(2)如果key不同（出现冲突），则将当前的key-value放入链表中
3. 获取时，直接找到hash值对应的下标，在进一步判断key是否相同，从而找到对应值。
4. 核心就是使用了数组的存储方式，然后将冲突的key的对象放入链表中，一旦发现冲突就在链表中做进一步的对比。

36、hashmap扩容

JDK1.8 HashMap两种扩容的情况。
1，当map实际数量等于threshold容量的阈值时，会进行两倍扩容。
2，当map中数组中某个桶的链表长度大于树形化阈值TREEIFY_THRESHOLD=8时，并且map元素的数量小于树形化最小容量MIN_TREEIFY_CAPACITY=64时候，容量进行两倍扩容。否则树形化阈值8并且map元素个数大于64时，进行链表转红黑树。

MIN_TREEIFY_CAPACITY=64，在树化过程时，当map长度小于这个值时，会再次扩容，不会走树化过程。

*那么预设元素的个数能够有效的提高hashmap的性能。比如说，我们有1000个元素new HashMap(1000), 但是理论上来讲new HashMap(1024)更合适，*

*不过上面annegu已经说过，即使是1000，hashmap也自动会将其设置为1024。 但是new HashMap(1024)还不是更合适的，因为0.75*  *1000 < 1000, 也就是说为了让0.75 * size > 1000, 

我们必须这样new HashMap(2048)才最合适，既考虑了&的问题，也避免了resize的问题。

37、List，Map， Set 三个接口

		List与Set都是单列元素的集合，它们有一个功共同的父接口Collection。
​	Set里面不允许有重复的元素，
​	存元素：add方法有一个boolean的返回值，当集合中没有某个元素，此时add方法可成功加入该元素时，则返回true；当集合含有与某个元素equals相等的元素时，
​	此时add方法无法加入该元素，返回结果为false。
​	取元素：没法说取第几个，只能以Iterator接口取得所有的元素，再逐一遍历各个元素。
​	List表示有先后顺序的集合，
​	存元素：多次调用add(Object)方法时，每次加入的对象按先来后到的顺序排序，也可以插队，即调用add(int index,Object)方法，就可以指定当前对象在集合中的存放位置。
​	取元素：方法1：Iterator接口取得所有，逐一遍历各个元素
​        	方法2：调用get(index i)来明确说明取第几个。
​	Map是双列的集合，存放用put方法:put(obj key,obj value)，每次存储时，要存储一对key/value，不能存储重复的key，这个重复的规则也是按equals比较相等。
​	取元素：用get(Object key)方法根据key获得相应的value。
​        	也可以获得所有的key的集合，还可以获得所有的value的集合，
​        	还可以获得key和value组合成的Map.Entry对象的集合。
​	List以特定次序来持有元素，可有重复元素。Set 无法拥有重复元素,内部排序。Map 保存key-value值，value可多值。

38、set里的元素不能重复的，那么用什么方法来区分重复与否?

39、 Fail-Fast 机制,多个线程对集合进行结构上的改变(crud)有可能产生Fail-Fast 机制		ConcurrentModificationException      [参考网址](https://blog.csdn.net/u012926924/article/details/50452411)

 遍历那些非线程安全的数据结构时，尽量使用迭代器 













# 面试问道的问题

## 多线程的锁有3种

1、NSLock
NSLock是Cocoa提供给我们最基本的锁对象，这也是我们经常使用的，除lock和unlock外，NSLock还提供了tryLock和lockBeforeDate:两个方法，前一个方法会尝试加锁，如果锁不可用（已经被锁住），并不会阻塞线程，直接返回NO。后一个方法则会在指定的Date之前尝试加锁，如果在指定的时间内都不能加锁，则返回NO
synchronized（互斥锁）
synchronized会创建一个异常捕获handler和一些内部的锁，所以使用@synchronized替换普通锁的代价是要付出更多的时间消耗
创建给给@synchronized指令的对象是一个用来区别保护块的唯一标识符。如果你在两个不同的线程里面执行上述方法，每次在一个线程传递了一个不同的对象给anObj参数，那么每次都将会拥有它的锁，并持续处理，中间不会被其他线程阻塞。然而如果你传递的是同一个对象，那么多个线程中的一个线程会首先获得该锁，而其他线程将会被阻塞直到第一个线程完成它的临界区
作为一个预防措施。@synchronized块隐式的添加一个异常处理例程来保护代码，该处理例程会在异常抛出的时候自动的释放互斥锁，这就意味着为了使用@synchronized指令，你必须在你的代码中启用异常处理。如果你不想让隐式的异常处理例程带来额外的开销，那么可以使用其他的锁
atomic
atomic只是给成员变量的set和get方法加了一个锁，防止多线程一直去读写这个成员变量。但这也仅仅是对读写的锁定，并不是线程安全。而且使用atomic比nonatomic慢了将近20倍
2、OSSpinlock
自旋锁
耗时最少
自旋锁几乎不进入内核，仅仅是重新加载自旋锁
如果自旋锁被占用时间在一百纳秒以内，性能还是比较高的，因为减少了代价较高的系统调用和一系列的上下文切换
但是该锁不是万能的，如果该锁占用的时间比较多的时候，使用该锁会导致占用的cpu较多
pthread_mutex
是底层的API，在各种加锁方式中属于性能比较高的
如果自旋锁占用的时间比较多，那么使用pthread是一个不错的选择
NSConditionLock（条件锁）
条件锁与特定的与用户定义的条件有关，它可以确保一个线程可以获取满足一定条件的锁
内部涉及到信号量机制，一旦一个线程获取锁以后，它可以放弃锁并设置相关条件，这时候其他锁竞争该锁
线程之间的竞争激烈，涉及到条件锁检测、线程间通信、系统调用，上下文切换比较频繁
NSRecursiveLock递归锁
NSRecursiveLock实际上定义的是一个递归锁，这个锁可以被同一线程多次请求，而不会引起死锁。这主要是用在循环或者递归操作中
总结：
如果只是粗略的使用锁，不考虑性能可以使用synchronized
如果对效率有较高的要求，采用OSSpinLock
因为pthread的锁也是使用OSSpinLock实现的，而且在OSSpinLock的实现过程中，并没有进入系统kernel，使用OSSpinLock可以节省系统调用和上下文切换
NSLock/NSConditionLock/NSRecursive耗时接近。220ms左右
dispatch_barrier_async的性能并没有我们想象中的纳闷好，这与线程同步调度开销有关

## redis数据类型

五种基本数据类型，分别是字符串（string），列表（list），集合（set），有序集合（zset）以及哈希（hash），

shiro中的权限管理
myibts中多对多查询用什么注解，二级缓存用什么标签
control中返回字符串用什么注解
active工作流中的问题

1、@Autowired：Spring注解 | @Resource：JDK注解 (推荐使用@Resource)
2、@Autowired 通过类型,自动装配(byType 默认按照Bean中的Class类型)
    @Resource 先通过参数名(byName  例如默认按照Bean中的id...)，
    而后是类型
3、@Autowired + @Qualifier("...") = @Resource(name="...")





## 流量限制

### 1、采用Nginx方法来限制 [参考网址](<https://www.cnblogs.com/hukey/p/10498544.html>)

### 2、springcloud 采用getway来限制

### 3、aop方式

## 幂等的处理方式

1、查询天然的幂等

2、唯一索引，防止新增脏数据

3、	token机制，防止重复提交

4、悲观锁 ，for update

5、乐观锁，通过版本号/时间戳实现，（where  version=12;）  ？？？<font color=#ee1111> 具体实现语句?????</font> 