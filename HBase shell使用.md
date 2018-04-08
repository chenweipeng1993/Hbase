HBase shell使用

HBase表操作命令介绍并显示

对表的操作
创建表，表结构，是否可用 删除 可用 是否失效 失效  
Create,Describe,is_enabled,Drop,Enable,isDisabled,Disable,List
Drop前先Disable

/bin/hbase shell 连接hbase的数据库

create 直接输入会有提示如何创建表信息
create 'test','info'
scan 'test' 查看表的数据
put 'test','0001','info:username','henry'  添加数据 put 表名 一行-rowkey 列簇:列名 值
put 'test','0001','info:age','20' 

describe 'test' 查看白哦的信息
list看到有哪些表
删除表
disable 'test'
is_enabled 'test' 查看表是否可用
drop 'test'

HBase表数据操作命令介绍并演示
求和 删除某一列的数据 get某一列/列的数据 put一行或者一列 全表扫描查全表数据  组合命令-初始化表-删除表并创建表
count delete get put scan truncate

count 'test' 对行数求和
get 'test','0001','info:username' 根据条件（表名，rowkey，列簇:列名）取出某一列的数据
delete 'test','0001','info:age' 删除某一列数据
truncate 'test' 
