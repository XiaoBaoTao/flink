# Day2

## 前置要求：
+ Java
  + 泛型
  + 接口和实现类
  + 匿名内部类
  + Lambda 
+ Redis
  + 存储实时计算结果

Kafka --> source --> filter --> sink -> redis 

## Flink流式计算思想

+ 程序结构
  + 数据源，比如kafka 
  + 数据转换，Transformation, 比如处理分析
  + 数据接收器Sink, 比如Redis或者Mysql 
+ Operator操作
  + 三种类型操作，三种Task 
  + 每个Operator可以设置并行度；
    + 每个事情，可以有多个人干活， 比如从Kafka,可以有多个同时消费数据；
  + **1条数据1条数据处理**，每条数据处理结束，进行输出；
  + 处理数据前，Task需要处于运行状态

## Flink 集群架构

每个Flink Job运行时，需要申请资源，想Flink Cluster集群申请资源。

分布式集群架构，主从架构； Master -> Slave 
+ 主节点，JobManager, 管理集群资源，接受客户端请求，分配资源Job给Task
+ 从节点， TaskManager， 只运行task任务，管理每个节点的资源；
    
      资源封装在资源槽slot中

本地运行： 
启动JM和TM， 提交Job到集群中运行，运行词频统计；


数仓开发：`Hive`

离线分析：`Spark` & `SparkSQL` 

实时分析：`Flink` & `Spark Stream`

## Flink Standalone集群

Flink client -> JobManager --> TaskManager(slot * 3)
                           <-- TaskManager(slot * 3)

任务都是运行在资源槽中；




























  

