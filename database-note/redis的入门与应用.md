## redis 的入门与应用
[redis的入门与应用](https://www.imooc.com/learn/809)

### 什么是 Redis
- Redis 是远程的
- Redis 是基于内存的
- Redis 是非关系型数据库（区别于关系型数据库，如mysql，关系型数据库必须定义存储用的数据字典，才能之后依据字典进行后续操作）

### Redis 的应用场景
- 缓存
- 队列
- 数据存储(Redis也有硬盘的持久化存储机制)

### 安装 
[参考官网的安装方式](https://redis.io/download)
```
$ wget http://download.redis.io/releases/redis-4.0.9.tar.gz
$ tar xzf redis-4.0.9.tar.gz
$ cd redis-4.0.9
$ make
$ make install
```

### 基本使用
```
# 查看 redis-server 的命令
$ redis-server --help

# 拷贝源码目录下的`redis.conf`文件去想要运行redis的目录下,并修改部分conf选项,例如 `demonize no`修改`no`为`yes`设置成后台启动,还有`port 6379`端口修改，默认为6379
$ cp /path/redis/redis.conf /var/test-redis/redis.conf

# 查看redis-server的安装目录
$ which redis-server

# 启动redis-server
$ /usr/local/bin/redis /var/test-redis/redis.conf

# 查看redis-server 启动状态
$ ps aux|grep redis-server

# 查看 redis-cli 的目录
$ which redis-cli

# 使用 redis-cli(假设运行的redis在conf中修改端口为7200)
$ redis-cli -h 127.0.0.1 -p 7200

# redis-cli 中查看 redis 信息
> info


```


### redis 的五种数据类型

|数据类型|存储的值|读写能力|
|------------|-------|------|
|String|可以是字符串，整数或浮点，统称为元素|对字符串操作 <br>对整数类型加减|
|List|一个序列集合且每个节点都包好了一个元素|序列两端推入，或弹出元素 修剪，查找或移除元素|
|Set|各不相同的元素|从集合中插入或者删除元素|
|Hash|有key-value的散列组，其中key是字符串，value是元素|按照key进行增加删除|
|Sort Set|带分数的score-value有序集合，其中score为浮点，value为元素|集合插入，按照分数范围查找|

```
# String `key value(string/int/float)`
127.0.0.1:7200> set string1 youngdee
OK
127.0.0.1:7200> get string1
"youngdee"
127.0.0.1:7200> set string2 4
OK
127.0.0.1:7200> get string2
"4"
# 这里的 incr 是自增的意思
127.0.0.1:7200> incr string2
(integer) 5
127.0.0.1:7200> get string2
"5"
# 这里的 decrby 是减去的意思
127.0.0.1:7200> decrby string2 2
(integer) 3
127.0.0.1:7200> get string2
"3"

# List
# 从列表左边推入数据12
127.0.0.1:7200> lpush list1 12
(integer) 1
127.0.0.1:7200> lpush list1 13
(integer) 2
# 从列表右侧获取
127.0.0.1:7200> rpop list1
"12"
# 下面说明了list不要求list集合中的值是唯一的，llen为显示集合的长度
127.0.0.1:7200> lpush list2 12
(integer) 1
127.0.0.1:7200> lpush list2 13
(integer) 2
127.0.0.1:7200> lpush list2 13
(integer) 3
127.0.0.1:7200> llen list2
(integer) 3

# Set
127.0.0.1:7200> sadd set1 12
(integer) 1
127.0.0.1:7200> scard set1
(integer) 1
127.0.0.1:7200> sadd set1 13
(integer) 1
127.0.0.1:7200> sadd set1 13
(integer) 0
127.0.0.1:7200> scard set1
(integer) 2
# 检查成员13
127.0.0.1:7200> sismember set1 13
(integer) 1
# 移除成员13
127.0.0.1:7200> srem set1 13
(integer) 1
127.0.0.1:7200> sismember set1 13
(integer) 0

# Hash
127.0.0.1:7200> hset hash1 key1 12
(integer) 1
127.0.0.1:7200> hget hash1 key1
"12"
127.0.0.1:7200> hset hash1 key2 13
(integer) 1
127.0.0.1:7200> hset hash1 key3 13
(integer) 1
# 查看hash集合的长度
127.0.0.1:7200> hlen hash1
(integer) 3
127.0.0.1:7200> hset hash1 key3 14
(integer) 0
127.0.0.1:7200> hget hash1 key3
"14"
# 一次获取多个 hash 集合数据
127.0.0.1:7200> hmget hash1 key1 key2
1) "12"
2) "13"

# Sort set
127.0.0.1:7200> zadd zset1 10.1 val1
(integer) 1
127.0.0.1:7200> zadd zset1 11.1 val2
(integer) 1
127.0.0.1:7200> zadd zset1 9.2 val3
(integer) 1
127.0.0.1:7200> zcard zset1
(integer) 3
127.0.0.1:7200> zrange zset1 0 2 withscores
1) "val3"
2) "9.1999999999999993"
3) "val1"
4) "10.1"
5) "val2"
6) "11.1"
127.0.0.1:7200> zrank zset1 val2
(integer) 2
127.0.0.1:7200> zadd zset1 12.2 val3
(integer) 0
127.0.0.1:7200> zrange zset1 0 2 withscores
1) "val1"
2) "10.1"
3) "val2"
4) "11.1"
5) "val3"
6) "12.199999999999999"
127.0.0.1:7200> zadd zset1 12.2 val2
(integer) 0
# 如果两个元素score一样，则按两个元素的字典顺序进行排序
127.0.0.1:7200> zrange zset1 0 2 withscores
1) "val1"
2) "10.1"
3) "val2"
4) "12.199999999999999"
5) "val3"
6) "12.199999999999999"
```
