# **Redis** （版本：3.2.100）

<font color=red size=6>help  ttl   //查看命令的作用</font>

<font color=red size=6>help @string   //查看string类型的命令</font>

## 命令

- 连接操作相关的命令
  •quit：关闭连接（connection）
  •auth：简单密码认证
  对value操作的命令
  •exists(key)：确认一个key是否存在
  •del(key)：删除一个key
  •type(key)：返回值的类型
  •keys(pattern)：返回满足给定pattern的所有key
  •randomkey：随机返回key空间的一个key
  •rename(oldname, newname)：将key由oldname重命名为newname，若newname存在则删除newname表示的key
  •dbsize：返回当前数据库中key的数目
  •expire：设定一个key的活动时间（s）
  •ttl：获得一个key的活动时间
  •select(index)：按索引查询
  •move(key, dbindex)：将当前数据库中的key转移到有dbindex索引的数据库
  •flushdb：删除当前选择数据库中的所有key
  •flushall：删除所有数据库中的所有key
  • **keys * 显示所有库中的key值遍历算法在key存在很多的时候，生产上使用容易造成卡顿阻塞**

  •keys aaa*   显示所有aaa 开头的key 

  •scan 0 match key99***** count 1000          **scan 参数提供了三个参数，第一个是 cursor 整数值，第二个是 key 的正则模式，第三个是遍历的 limit hint。第一次遍历时，cursor值为0，然后将返回结果中第一个整数值作为下一次遍历的 cursor。一直遍历到返回的 cursor 值为 0 时结束**

  

- 对String操作的命令   （<font color=#0129ff size=2>key value 有无双引号都一样，且key是唯一的</font>）
  •set(key, value)：给数据库中名称为key的string赋予值value，<font color=#0129ff size=2>当key已存在是，覆盖value值</font>
  •get(key)：返回数据库中名称为key的string的value
  •getset(key, value)：先获取（get ）后（set），返回的是get的值
  •mget(key1, key2,…, key N)：返回库中多个string（它们的名称为key1，key2…）的value
  •setnx(key, value)：如果不存在名称为key的string，则向库中添加string，名称为key，值为value
  •setex(key, time, value)：向库中添加string（名称为key，值为value）同时，设定过期时间time（秒）若原来已经存在key则覆盖掉，每次都是新添加的
  •mset(key1, value1, key2, value2,…key N, value N)：同时给多个string赋值，名称为key i的string赋值value i
  •msetnx(key1, value1, key2, value2,…key N, value N)：如果所有名称为key i的string都不存在，则向库中添加string，名称key i赋值为value i
  •incr(key)：名称为key的string增1操作 <font color=#0000ff size=2>string的值必须为数字</font>
  •incrby(key, integer)：名称为key的string增加integer
  •decr(key)：名称为key的string减1操作 <font color=#0000ff size=2>string的值必须为数字</font>
  •decrby(key, integer)：名称为key的string减少integer
  •append(key, value)：名称为key的string的值附加value
  •substr(key, start, end)：返回名称为key的string的value的子串 相当于java中的string substr的操作

  

- 对List操作的命令
  •rpush(key, value)：在名称为key的list尾添加一个值为value的元素 。<font color=#0000ff size=2>（右边添加）</font>
  •lpush(key, value)：在名称为key的list头添加一个值为value的元素
  •llen(key)：返回名称为key的list的长度
  •lrange(key, start, end)：返回名称为key的list中start至end之间的元素    （<font color=red size=2>下标从0开始，下同</font>）
  •ltrim(key, start, end)：截取名称为key的list，保留start至end之间的元素  
  •lindex(key, index)：返回名称为key的list中index位置的元素
  •lset(key, index, value)：给名称为key的list中index位置的元素赋值为value
  • **lrem(key, count, value)：删除count个名称为key的list中值为value的元素。count为0，删除所有值为value的元素，count>0从头至尾删除count个值为value的元素，count<0从尾到头删除|count|个值为value的元素**
  •lpop(key)：返回并删除名称为key的list中的首元素
  •rpop(key)：返回并删除名称为key的list中的尾元素
  •blpop(key1, key2,… key N, timeout)：lpop命令的block版本。即当timeout为0时，若遇到名称为keyi的list不存在或该list为空，则命令结束。如果timeout>0，则遇到上述情况时，等待timeout秒，如果问题没有解决，则对key
  i+1开始的list执行pop操作
  •brpop(key1, key2,… key N, timeout)：rpop的block版本。参考上一命令
  •rpoplpush(srckey, dstkey)：返回并删除名称为srckey的list的尾元素，并将该元素添加到名称为dstkey的list的头部

  

- 对Set操作的命令 （<font color=#0000ff size=2 >set 中不会存在重复的member值</font>）
  •sadd(key, member)：向名称为key的set中添加元素member  
  •srem(key, member) ：删除名称为key的set中的元素member
  •spop(key) ：随机返回并删除名称为key的set中一个元素
  •smove(srckey, dstkey, member) ：将member元素从名称为srckey的集合移到名称为dstkey的集合
  •scard(key) ：返回名称为key的set的基数
  •sismember(key, member) ：测试member是否是名称为key的set的元素 ，返回1 存在 ，0 不存在
  •sinter(key1, key2,…key N) ：求交集
  •sinterstore(dstkey, key1, key2,…key N) ：求交集并将交集保存到dstkey的集合
  •sunion(key1, key2,…key N) ：求并集
  •sunionstore(dstkey, key1, key2,…key N) ：求并集并将并集保存到dstkey的集合
  •sdiff(key1, key2,…key N) ：求差集
  •sdiffstore(dstkey, key1, key2,…key N) ：求差集并将差集保存到dstkey的集合
  •smembers(key) ：返回名称为key的set的所有元素
  •srandmember(key) ：随机返回名称为key的set的一个元素

  

- 对zset（sorted set）操作的命令
  •zadd(key, score, member)：向名称为key的zset中添加元素member，score用于排序。如果该元素已经存在，则根据score更新该元素的顺序
  •zrem(key, member) ：删除名称为key的zset中的元素member
  •zincrby(key, increment, member) ：如果在名称为key的zset中已经存在元素member，则该元素的score增加increment；否则向集合中添加该元素，其score的值为increment
  •zrank(key, member) ：返回名称为key的zset（元素已按score从小到大排序）中member元素的rank（即index，从0开始），若没有member元素，返回“nil”
  •zrevrank(key, member) ：返回名称为key的zset（元素已按score从大到小排序）中member元素的rank（即index，从0开始），若没有member元素，返回“nil”
  •zrange(key, start, end)：返回名称为key的zset（元素已按score从小到大排序）中的index从start到end的所有元素
  •zrevrange(key, start, end)：返回名称为key的zset（元素已按score从大到小排序）中的index从start到end的所有元素
  •zrangebyscore(key, min, max)：返回名称为key的zset中score >= min且score < = max的所有元素
  •zcard(key)：返回名称为key的zset的基数
  •zscore(key, element)：返回名称为key的zset中元素element的score
  •zremrangebyrank(key, min, max)：删除名称为key的zset中rank >= min且rank < = max的所有元素
  •zremrangebyscore(key, min, max) ：删除名称为key的zset中score >= min且score < = max的所有元素
  •zunionstore / zinterstore(dstkeyN, key1,…,keyN, WEIGHTS w1,…wN, AGGREGATESUM|MIN|MAX)：对N个zset求并集和交集，并将最后的集合保存在dstkeyN中。对于集合中每一个元素的score，在进行AGGREGATE运算前，都要乘以对于的WEIGHT参数。如果没有提供WEIGHT，默认为1。默认的AGGREGATE是SUM，即结果集合中元素的score是所有集合对应元素进行SUM运算的值，而MIN和MAX是指，结果集合中元素的score是所有集合对应元素中最小值和最大值

  

- 对Hash操作的命令
  •hset(key, field, value)：向名称为key的hash中添加元素fieldvalue
  •hget(key, field)：返回名称为key的hash中field对应的value
  •hmget(key, field1, …,field N)：返回名称为key的hash中field i对应的value
  •hmset(key, field1, value1,…,field N, value N)：向名称为key的hash中添加元素field i< —>value i
  •hincrby(key, field, integer)：将名称为key的hash中field的value增加integer
  •hexists(key, field)：名称为key的hash中是否存在键为field的域
  •hdel(key, field)：删除名称为key的hash中键为field的域
  •hlen(key)：返回名称为key的hash中元素个数
  •hkeys(key)：返回名称为key的hash中所有键
  •hvals(key)：返回名称为key的hash中所有键对应的value
  •hgetall(key)：返回名称为key的hash中所有的键（field）及其对应的value

  

- 持久化
  •save：将数据同步保存到磁盘
  •bgsave：将数据异步保存到磁盘
  •lastsave：返回上次成功将数据保存到磁盘的Unix时戳
  •shundown：将数据同步保存到磁盘，然后关闭服务

- 远程服务控制
  •info：提供服务器的信息和统计
  •monitor：实时转储收到的请求
  •slaveof：改变复制策略设置
  •config：在运行时配置Redis服务器

连接操作相关的命令
•quit：关闭连接（connection）
•auth：简单密码认证
对value操作的命令
•exists(key)：确认一个key是否存在
•del(key)：删除一个key
•type(key)：返回值的类型
•keys(pattern)：返回满足给定pattern的所有key
•randomkey：随机返回key空间的一个key
•rename(oldname, newname)：将key由oldname重命名为newname，若newname存在则删除newname表示的key
•dbsize：返回当前数据库中key的数目
•expire：设定一个key的活动时间（s）
•ttl：获得一个key的活动时间
•select(index)：按索引查询
•move(key, dbindex)：将当前数据库中的key转移到有dbindex索引的数据库
•flushdb：删除当前选择数据库中的所有key
•flushall：删除所有数据库中的所有key
• keys * 显示所有库中的key值遍历算法在key存在很多的时候，生产上使用容易造成卡顿阻塞

•keys aaa*   显示所有aaa 开头的key 

scan 0 match key99***** count 1000          scan 参数提供了三个参数，第一个是 cursor 整数值，第二个是 key 的正则模式，第三个是遍历的 limit hint。第一次遍历时，cursor值为0，然后将返回结果中第一个整数值作为下一次遍历的 cursor。一直遍历到返回的 cursor 值为 0 时结束



对String操作的命令   （<font color=#0129ff size=2>key value 有无双引号都一样，且key是唯一的</font>）
•set(key, value)：给数据库中名称为key的string赋予值value，<font color=#0129ff size=2>当key已存在是，覆盖value值</font>
•get(key)：返回数据库中名称为key的string的value
•getset(key, value)：先获取（get ）后（set），返回的是get的值
•mget(key1, key2,…, key N)：返回库中多个string（它们的名称为key1，key2…）的value
•setnx(key, value)：如果不存在名称为key的string，则向库中添加string，名称为key，值为value
•setex(key, time, value)：向库中添加string（名称为key，值为value）同时，设定过期时间time（秒）
•mset(key1, value1, key2, value2,…key N, value N)：同时给多个string赋值，名称为key i的string赋值value i
•msetnx(key1, value1, key2, value2,…key N, value N)：如果所有名称为key i的string都不存在，则向库中添加string，名称key i赋值为value i
•incr(key)：名称为key的string增1操作 <font color=#0000ff size=2>string的值必须为数字</font>
•incrby(key, integer)：名称为key的string增加integer
•decr(key)：名称为key的string减1操作 <font color=#0000ff size=2>string的值必须为数字</font>
•decrby(key, integer)：名称为key的string减少integer
•append(key, value)：名称为key的string的值附加value
•substr(key, start, end)：返回名称为key的string的value的子串 相当于java中的string substr的操作



对List操作的命令
•rpush(key, value)：在名称为key的list尾添加一个值为value的元素 。<font color=#0000ff size=2>（右边添加）</font>
•lpush(key, value)：在名称为key的list头添加一个值为value的元素
•llen(key)：返回名称为key的list的长度
•lrange(key, start, end)：返回名称为key的list中start至end之间的元素    （<font color=red size=2>下标从0开始，下同</font>）
•ltrim(key, start, end)：截取名称为key的list，保留start至end之间的元素  
•lindex(key, index)：返回名称为key的list中index位置的元素
•lset(key, index, value)：给名称为key的list中index位置的元素赋值为value
• **lrem(key, count, value)：删除count个名称为key的list中值为value的元素。count为0，删除所有值为value的元素，count>0从头至尾删除count个值为value的元素，count<0从尾到头删除|count|个值为value的元素**
•lpop(key)：返回并删除名称为key的list中的首元素
•rpop(key)：返回并删除名称为key的list中的尾元素
•blpop(key1, key2,… key N, timeout)：lpop命令的block版本。即当timeout为0时，若遇到名称为keyi的list不存在或该list为空，则命令结束。如果timeout>0，则遇到上述情况时，等待timeout秒，如果问题没有解决，则对key
i+1开始的list执行pop操作
•brpop(key1, key2,… key N, timeout)：rpop的block版本。参考上一命令
•rpoplpush(srckey, dstkey)：返回并删除名称为srckey的list的尾元素，并将该元素添加到名称为dstkey的list的头部



对Set操作的命令
•sadd(key, member)：向名称为key的set中添加元素member
•srem(key, member) ：删除名称为key的set中的元素member
•spop(key) ：随机返回并删除名称为key的set中一个元素
•smove(srckey, dstkey, member) ：将member元素从名称为srckey的集合移到名称为dstkey的集合
•scard(key) ：返回名称为key的set的基数
•sismember(key, member) ：测试member是否是名称为key的set的元素
•sinter(key1, key2,…key N) ：求交集
•sinterstore(dstkey, key1, key2,…key N) ：求交集并将交集保存到dstkey的集合
•sunion(key1, key2,…key N) ：求并集
•sunionstore(dstkey, key1, key2,…key N) ：求并集并将并集保存到dstkey的集合
•sdiff(key1, key2,…key N) ：求差集
•sdiffstore(dstkey, key1, key2,…key N) ：求差集并将差集保存到dstkey的集合
•smembers(key) ：返回名称为key的set的所有元素
•srandmember(key) ：随机返回名称为key的set的一个元素



对zset（sorted set）操作的命令
•zadd(key, score, member)：向名称为key的zset中添加元素member，score用于排序。如果该元素已经存在，则根据score更新该元素的顺序
•zrem(key, member) ：删除名称为key的zset中的元素member
•zincrby(key, increment, member) ：如果在名称为key的zset中已经存在元素member，则该元素的score增加increment；否则向集合中添加该元素，其score的值为increment
•zrank(key, member) ：返回名称为key的zset（元素已按score从小到大排序）中member元素的rank（即index，从0开始），若没有member元素，返回“nil”
•zrevrank(key, member) ：返回名称为key的zset（元素已按score从大到小排序）中member元素的rank（即index，从0开始），若没有member元素，返回“nil”
•zrange(key, start, end)：返回名称为key的zset（元素已按score从小到大排序）中的index从start到end的所有元素
•zrevrange(key, start, end)：返回名称为key的zset（元素已按score从大到小排序）中的index从start到end的所有元素
•zrangebyscore(key, min, max)：返回名称为key的zset中score >= min且score < = max的所有元素
•zcard(key)：返回名称为key的zset的基数
•zscore(key, element)：返回名称为key的zset中元素element的score
•zremrangebyrank(key, min, max)：删除名称为key的zset中rank >= min且rank < = max的所有元素
•zremrangebyscore(key, min, max) ：删除名称为key的zset中score >= min且score < = max的所有元素
•zunionstore / zinterstore(dstkeyN, key1,…,keyN, WEIGHTS w1,…wN, AGGREGATESUM|MIN|MAX)：对N个zset求并集和交集，并将最后的集合保存在dstkeyN中。对于集合中每一个元素的score，在进行AGGREGATE运算前，都要乘以对于的WEIGHT参数。如果没有提供WEIGHT，默认为1。默认的AGGREGATE是SUM，即结果集合中元素的score是所有集合对应元素进行SUM运算的值，而MIN和MAX是指，结果集合中元素的score是所有集合对应元素中最小值和最大值



对Hash操作的命令
•hset(key, field, value)：向名称为key的hash中添加元素fieldvalue
•hget(key, field)：返回名称为key的hash中field对应的value
•hmget(key, field1, …,field N)：返回名称为key的hash中field i对应的value
•hmset(key, field1, value1,…,field N, value N)：向名称为key的hash中添加元素field i< —>value i
•hincrby(key, field, integer)：将名称为key的hash中field的value增加integer
•hexists(key, field)：名称为key的hash中是否存在键为field的域
•hdel(key, field)：删除名称为key的hash中键为field的域
•hlen(key)：返回名称为key的hash中元素个数
•hkeys(key)：返回名称为key的hash中所有键
•hvals(key)：返回名称为key的hash中所有键对应的value
•hgetall(key)：返回名称为key的hash中所有的键（field）及其对应的value



持久化
•save：将数据同步保存到磁盘
•bgsave：将数据异步保存到磁盘
•lastsave：返回上次成功将数据保存到磁盘的Unix时戳
•shundown：将数据同步保存到磁盘，然后关闭服务

远程服务控制
•info：提供服务器的信息和统计
•monitor：实时转储收到的请求
•slaveof：改变复制策略设置
•config：在运行时配置Redis服务器





## 1、场景

### 1、查询用户是否连续签到

```js
// SETBIT  用户ID+月份  日期  value

SETBIT  Sign:2094592473:202110  0       1
SETBIT  Sign:2094592473:202110  7       1
SETBIT  Sign:2094592473:202110  8       1
SETBIT  Sign:2094592473:202110  9       0
SETBIT  Sign:2094592473:202110  10      1
SETBIT  Sign:2094592473:202110  11      1
SETBIT  Sign:2094592473:202110  12      1
SETBIT  Sign:2094592473:202110  13      0
SETBIT  Sign:2094592473:202110  14      1
SETBIT  Sign:2094592473:202110  15      1
SETBIT  Sign:2094592473:202110  16      1
SETBIT  Sign:2094592473:202110  17      1
SETBIT  Sign:2094592473:202110  18      1
SETBIT  Sign:2094592473:202110  19      1
SETBIT  Sign:2094592473:202110  20      1

//  获取10月31天的签到数据
BITFIELD Sign:2094592473:202110 get u31 0 7
1) (integer) 14547968

// 转换成二进制
110111011111110000000000

// 判断是否有连续7天的1
```

### 2、查询用户10月 签到总次数

```js
BITCOUNT Sign:2094592473:202110
```



###  3、指定时间内，判断多少人签到连续签到成功

``` js
// SETBIT 日期  用户ID  value

SETBIT 20211015 10 1
SETBIT 20211016 10 1
SETBIT 20211017 10 1
SETBIT 20211018 10 1

SETBIT 20211015 20 1
SETBIT 20211016 20 0
SETBIT 20211017 20 1
SETBIT 20211018 20 1

SETBIT 20211015 30 1
SETBIT 20211016 30 1
SETBIT 20211017 30 1
SETBIT 20211018 30 1

SETBIT 20211015 40 1
SETBIT 20211016 40 0
SETBIT 20211017 40 0
SETBIT 20211018 40 1

BITOP AND destmap 20211015 20211016 20211017 20211018
//获取前8天签到的数据
bitfield 888:202205 get u8 0             
BITCOUNT destmap
2

```




