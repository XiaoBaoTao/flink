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

流处理，`一条一条`数据处理, 每次处理`一条`数据；流水线；

Hadoop -> Spark -> Flume, Redis, Kafka, Hbase -> Flink

实时的概念为，只要数据一产生，立即处理输出；

大数据中使用Redis内存数据库的场景

    + 存储实时计算结果
      + Flink将实时计算的结果存储在redis, 前端从redis中读取
    + 缓存黑名单或者配置监控
        + 实时监控

***

1.12.0之前，流批API是分开的； 流处理：

+ 之后的版本，都可以用DataStream#Operator来处理；

批处理

+ 核心类： DataSet # Operator

1.12.0之后，使用1套API, 核心类 DataStream, 设置模式即可；

学习以1.13版本；

### Flink优秀的四点：

+ State
+ CheckPoint
+ Window
+ Time

`Flink Table API 和SQL, 推荐使用SQL编程分析`

分享：

1. [https://flink.apache.org/](https://flink.apache.org/)
1. [https://github.com/apache/flink](https://github.com/apache/flink)

## Flink介绍

Stateful Computations over Data Streams

大规模，海量数据分析框架:

+ 分布式
+ 并行计算

<img src="https://flink.apache.org/img/flink-home-graphic.png">

### 处理对象

+ 数据流 , 将数据抽象到`Data Streams`中， Java中的抽象类为`DataStream`
+ 数据流分为两种，
    + 有界数据流: 批处理, 有开始时间和结束时间
    + 无界数据流: 流处理， 无结束时间

### 如何处理

+ `stateful computation` <状态计算>
+ ** 每次计算过程中的中间值，即为状态 **


     Apache Flink is a framework and distributed processing engine for stateful computations over unbounded and bounded data streams. 
     Flink has been designed to run in all common cluster environments, 
     perform computations at in-memory speed and at any scale.

柏林工业大学实验室@2014年; 

### 流式数据处理的思想
网站 -> kafka -> source -> filter -> map -> 分组聚合 -> sink -> redis

+ 产生一条数据，就处理一条数据，并且是实时处理； 
+ Flink流式计算程序中， 无论source, transformation, 还是Sink, 都是由多个任务来进行操作的。 并行计算
+ 先运行Task, 数据一来立马开始计算; 


Source ——> DataStream -> map, flatmap, filter -> Sink. 

Flink处理任务之前，需要分配资源；

### 算子(Operator)的概念

Source Operator -> Transformation Operator -> Sink Operator 

+ 每个算子可以有多个并行度, 多个Task并行计算；
+ 算子之间就是数据流

### Flink的应用场景

实时数仓，实时监控，实时报表，流数据分析；


## Flink的安装部署

### 架构

Flink Client -> Submit Jobs -> Flink Cluster -> 分配资源

管理资源， 分配资源给Job运行；


    client -> JobManager(主节点)  -->     TaskManager   slot(资源槽T) * 3
                                 -->     TaskManager   slot(资源槽T) * 3
                                 -->     TaskManager   slot(资源槽T) * 3 




### Flink运行模式

本地模式： JobManager & TaskManager 

集群模式  Yarn  (国内主要)

容器模式  K8S






































