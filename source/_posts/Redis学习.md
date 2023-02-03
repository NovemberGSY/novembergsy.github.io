---
title: Redis 学习
category:  Java
---
### Redis学习

#### 1、Redis是什么？

-   **Redis**的全称是**(REmote DIctionary Server 远程字典服务)**，是一个由Salvatore Sanfilippo写的key-value存储系统。

- Redis是一个开源的，使用ANSI（C语言标准） C语言编写，遵守BSD（“*Berkeley* Software Distribution”伯克利软件发行版）协议，支持网络，可基于内存亦可持久化的日志型，Key-Value数据库，并且提供多种语言的API。

- Redis通常被称为数据结构服务器，因为其可以存储的值（Value）可以是

  - String 字符串
  - Hash 哈希
  - List 列表
  - Sets 集合
  - Sorted sets 有序集合

  ---

  

相关链接：

Redis 官网：https://redis.io/

Redis 在线测试：http://try.redis.io/

Redis 命令参考：http://doc.redisfans.com/

#### 2、Redis能做什么？

1. ##### Redis 与其他 key - value 缓存产品有以下三个特点：

- Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
- Redis不仅仅支持简单的 key-value 类型的数据，同时还提供 list，set，zset，hash等数据结构的存储
- Redis支持数据的备份，即master-slave模式的数据备份

#### 3、为什么选择使用Redis？

##### 关于Redis的优势：

-  性能极高 —— Redis能读的速度是110000次/s，写的速度是81000次/s。
- 丰富的数据类型 —— Redis支持二进制案例的String，Lists，Hashes，Sets 及 Ordered Sets 数据类型操作。
- 原子 —— Redis的所有操作系统都是原子性的，意思就是要么成功执行，要么失败完全不执行。单个操作是原子性的。
- 丰富的特性  —— Redis还支持 publish/subscribe，通知，key过期等等特性。

##### Redis与其他key - value 存储有什么不同？

- Redis更为复杂的数据结构并且提供对这些数据结构的原子性操作，这是一个不同于其他数据库的进化路径。Redis的数据类型都是基于基本数据结构的，同时对于程序眼透明，无需进行额外的抽象。
- Redis运行在内存中但是可以持久化到磁盘，所以在对不同数据集进行高速读写时需要权衡内存，因为数据量不能大于硬件内存。在内存数据库方面的另一个优点是，相比在磁盘上相同的复杂数据结构，在内存中操作起来非常简单，这样Redis可以做很多内部复杂性很强的事情。

#### 4、Redis的相关命令

- 启动Redis（需要切换到安装Redis的bin/目录下）

```shell
$ ./redis-server   启动Redis
```

启动成功后的界面如下：



![redis-install1](https://www.runoob.com/wp-content/uploads/2014/11/redis-install1.png)

- 查看Redis状态（是否启动，是否使用成功）

  ```shell
  $ redis-cli  该命令会链接本地的Redis服务
  ```

- 关闭Redis

  ```shell
  $ redis-cli 进入Redis服务
  $ shutdown save｜nosave 	系统会提示保存还是不保存
  ```

关于 save 和 nosave

- **SHUTDOWN SAVE**能够在即使没有配置持久化的情况下强制数据库存储.
- **SHUTDOWN NOSAVE** 能够在配置一个或者多个持久化策略的情况下阻止数据库存储. (你可以假想它为一个中断服务的 **ABORT** 命令).

