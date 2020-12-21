# mysql

## mysql中REGEXP正则表达式使用

​		https://blog.csdn.net/haitunmin/article/details/75234231

![mysql中的REGEXP匹配规则](assets/mysql%E4%B8%AD%E7%9A%84REGEXP%E5%8C%B9%E9%85%8D%E8%A7%84%E5%88%99.PNG)

## 分页查询

```mysql

/** 时间 2.681s   type all
*/
EXPLAIN
SELECT `name`,id ,a.time
FROM test a where  id LIMIT 3618156,10;


/*时间 0.086s id的值具体情况具体考虑
type range
*/
EXPLAIN
SELECT `name`,id ,a.time
FROM test a where id>1326542914447071910 and
id LIMIT 0,10;
```

## 频繁多表进行删除时，需要进行索引的重构，造成的原因为

![image-20201207014815801](assets/image-20201207014815801.png)



