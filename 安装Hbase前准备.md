# Hbase
官网地址：http://hbase.apache.org/
http://archive.apache.org/dist/
cdh版本
http://archive.cloudera.com/cdh5/

RegionServer master zookeeper hdfs
分区

表结构模型
面向列簇 个人信息 工作经历
列 姓名 年龄 电话 工作1 工作2 工作3

数据模型
列簇 一张表的列簇不会超过5个
  每个列簇中的列数没有限制
  列只有插入数据后存在
  列在列簇中是有序的

hbase表和关系型数据库结构的对比
列动态增加
数据自动切分
高并发读写
不支持条件查询  复杂查询-关系型数据优势

安装说明
jdk1.7以上
hadoop-2.5.0以上 
zookeeper-3.4.5以上 cdh版本 zookeeper-3.4.5-cdh5.10.0.tar.gz
hbase-0.98.6-cdh5.3.0.tar.gz

--hadoop安装
解压
配置hadoop-env.sh

core-site.xml
配置访问hdfs的地址
fs.defaultFS
hdfs://主机名:9000  9000是默认的端口
vim /etc/hosts
加上主机名和ip的映射
配置一个temp目录 在linux上创建目录mkdir -p data/tmp
hadoop.temp.dir
/opt/modules/hadoop-2.5.0/data/tmp

hdfs-site.xml
副本数
dfs.replication
1
用户访问权限的配置
dfs.permissions.enabled
false

配置slaves
datdanode节点机器是放在哪里，和namenode放在同一个机器上，单节点
直接写主机名

不需要配置mapreduce和yarn，因为没有分析，只有存储

格式化
bin/hdfs namenode -format 
启动
sbin/hadoop-daemon.sh start namenode
启动
sbin/hadoop-daemon.sh start datanode 
访问的端口号是50070
http://主机名:50070

---zookeeper分布式安装
tar -zxf zookeeper-3.4.5-cdh5.10.0.tar.gz -C /opt/modules/
配置zoo.cfg文件
修改dataDir=/opt/modules/zookeeper-3.4.5-cdh5.10.0/zkData
clientPort=2181
server.1=主机名1:2881:3881
server.2=主机名2:2882:3882
server.3=主机名3:2883:3883
在服务目录下创建一个文件myid-在上面的那个datdaDir目录下
touch myid 
vim myid 
1

将一台配置好的zk复制到另外的机器上
scp -r zookeeper-3.4.5-xxx/ 主机名2:/opt/modules
修改myid为2
同理第三台

启动zk
bin/zkServer.sh start

