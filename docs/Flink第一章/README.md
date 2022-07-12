# 第一章

## 前言

大数据发展趋势：

+ SQL化
+ 平台化
+ 弱代码化

大数据开发的编程语言：

+ SQL 大数据分析使用SQL
+ Java语言 大数据框架编程语言
    + Scala 基于JVM的语言
+ Python语言
    + Spark, Flink 支持Python语言编程

+ SQL是趋势， 将MySQL和HiveSQL搞懂；

Flink 2019年被Alibaba收购，发展方在XZ啧啧啧自知则知之安全q'w'Q向是SQL化； 目前还是主要用Java开发Flink. 课程一个月左右

代码要敲，而且要多多敲， agree!

分而治之，大数据的核心。

常规的流程为：

1. 创建类，设置属性
2. 调用方法

### 离线分析：

+ 存储， Hive, Hadoop
    + 管理元数据(表，数据)
+ 计算， MR, Spark
    + Hive将SQL转换为MR,或者Spark

批处理；

### 实时计算:

+ 存储，Kafka
+ 计算，Flink, Spark(StructuredStreaming)
    + 依赖YARN
    + 依赖HDFS

流处理，一条一条数据处理；流水线；

Hadoop -> Spark -> Flume, Redis, Kafka, Hbase -> Flink

实时的概念为，只要数据一产生，立即处理输出；

大数据中使用Redis内存数据库的场景

    + 存储实时计算结果
      + Flink将实时计算的结果存储在redis, 前端从redis中读取
    + 缓存黑名单或者配置监控
        + 实时监控

***



  




