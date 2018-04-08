Hbase是一个分布式的数据库
主要作用：海量数据的存储和海量数据的准实时查询
-、HBase的应用场景和特点
>>应用场景
交通 金融 电商 移动 

>>Hbase的特点
容量大
列式存储
多版本
扩展性
稀疏性
高性能
可靠性

二、Hbase的定义和定位
>>官方对于Hbase的概念描述
>>hadoop生态系统中对于Hbase的定位

三、Hbase的架构体系和设计模型
>>服务架构体系
1）hbase的主要进程：master regionserver
2）hbase所依赖的两个外部的服务：zookeeper HDFS

>>设计模型
1）表结构
2）表数据

四、Hbase的安装部署
>>Hbase部署条件
1）JDK1.7以上
2）Hadoop2.5.X以上的版本
3）zookeeper3.4.x以上的版本

五、Hbase shell
>>DDL
  create describle disable enable drop list
>>DML
  put count scan get delete
