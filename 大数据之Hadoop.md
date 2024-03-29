# 大数据之 Hadoop

## 一、大数据概论

### 1、大数据概念

大数据（Big Data）是指无法在一定时间范围内用常规软件工具进行捕捉、管理、和处理数据的集合，是需要新处理模式才能具有更强的决策力、洞察发现力和流程优化能力的海量、高增长率和多样化的信息资产。

其实大数据主要解决的就是两个事：

> 1、海量数据的存储
>
> 2、海量数据的分析计算

**注：**

> 这个常规软件工具指的就是我们之前使用的 JavaEE 技术，比如说 mysql 、 mybatis ，mysql 中大概能存 500-1000 万条数据，但是大数据一般都是亿级别的，所以这个数据量 mysql 根本存不了，就算存了，检索效率也非常低。

### 2、大数据特点

> - Volume （大量）
>   - 产生的数据量很大
> - Velocity （高速）
>   - 产生数据的速度很快
> - Variety （多样）
>   - 这种类型的多样性也让数据被分为结构化数据和非结构化数据。相对于以往便于存储的以数据库/文本为主的结构化数据，非结构化数据越来越多，包括网络日志、音频、图片、地理位置信息等，这些多类型的数据对数据的处理能力提出了更高的要求
> - Value （低价值密度）
>   - 价值密度的高低与数据总量的大小成反比。比如说警察抓小偷，他只关心监控中那几分钟的视频，如何快速对有价值数据提纯，成为目前大数据背景下待解决的难题。

### 3、大数据应用场景

> - 物流仓储：大数据分析系统助力商家精细化运营、提升销量、节约成本
> - 零售：分析用户消费习惯，为用户购买商品提供方便，从而提升商品销量
> - 旅游：深度结合大数据能力与旅游行业需求，共建旅游产业智慧管理、智慧服务和智慧营销的未来
> - 商品广告推荐：给用户推荐可能喜欢的商品

## 二、从 Hadoop 框架讨论大数据生态

#### 1、Hadoop 是什么

> - Hadoop 是一个由 Apache 基金会所开发的分布式系统基础架构
> - 主要解决海量数据的存储和海量数据的分析计算问题
> - 广义上来说，Hadoop 通常是指一个更广泛的概念-Hadoop 生态圈

#### 2、Hadoop 发展历史

> 1. Lucene 框架是 『Doug Cutting』开创的开源软件，用 Java 编写，实现与 Google 类似的全文搜索功能，它提供了全文搜索引擎
> 2. 2001 年底 Lucene 成为 Apache 基金会的一个子项目
> 3. 对于海量数据的场景，Luncene 面对与 Google 同样的困难，*存储数据困难，检索速度慢*
> 4. 学习和模仿 Google 解决这些问题的办法：微型版 Nutch
> 5. 2003-2004 年，Google 公开了部分 GFS 和 MapReduce 思想的细节，以此为基础 『Doug Cutting』等人用了两年业余时间实现了 DFS 和 MapReduce 机制，使 Nutch 性能飙升
> 6. 2005 年 Hadoop 作为 Luncene 的子项目 Nutch 的一部分正式引入 Apache 基金会
> 7. 2006 年 3 月份， Map-Reduce 和 Nutch Distributed File System（NDFS）分别被纳入成为 Hadoop 的项目中
> 8.  Hadoop 的 logo 来源于 『Doug Cutting』 儿子的玩具大象
> 9. Hadoop 就此诞生并迅速发展，标志的大数据时代来临

#### 3、Hadoop 三大发行版本

Hadoop 三大发行版本：『Apache』 、『Cloudera』 、『Hortonworks』

> - Apache 版本是最原始的版本，对于入门学习最好
> - Cloudera 在大型互联网企业中用的较多
> - Hortonworks 文档较好

#### 4、Hadoop 的优势

> - 高可靠性
>   - Hadoop 底层维护了多个数据副本，所以即使 Hadoop 某个计算元素或存储出现故障，也不会导致数据的丢失
> - 高扩展性
>   - 在集群间分配任务数据，可方便的扩展数以千计的节点
> - 高效性
>   - 在 MapReduce 思想下，Hadoop 是并行工作的，以加快任务处理速度
> - 高容错性
>   - 能够自动将失败的任务重新分配

#### 5、Hadoop1.X 和 Hadoop2.X 的区别

> 在 Hadoop1.x 时代，Hadoop 中的 MapReduce 同时处理业务逻辑运算和资源的调度，耦合性较大。在 Hadoop2.x 时代，增加了 Yarn。Yarn 只负责资源的调度，MapReduce 只负责运算。

#### 6、Hadoop 组成

1）、HDFS 架构概述

> - NameNode（nn）：存储文件的元数据。如：文件名，文件的目录结构，文件属性（生成时间、副本数、文件权限），以及每个文件的块列表和块所在的 DataNode 等
> - DataNode（dn）：在本地文件系统存储文件块数据，以及块数据的校验和
> - Secondary NameNode（2nn）：用来监控 HDFS 状态的辅助后台程序，每隔一段时间获取 HDFS 元数据的快照

2）、YARN 架构概述



![YARN架构图](https://shp-notes-1257820375.cos.ap-chengdu.myqcloud.com/shp-hadoop/YARN%E6%9E%B6%E6%9E%84%E5%9B%BE.png?q-sign-algorithm=sha1&q-ak=AKID7zjHweurnnEHqmB67L0Ulw3tmNnc1stn&q-sign-time=1562505220;1562508820&q-key-time=1562505220;1562508820&q-header-list=&q-url-param-list=&q-signature=f3a341a0b07d3942d69726f7bce10108d802398c&x-cos-security-token=07e7a2523678a7b4827d1e88033249ac722dfdf110001)



3）、MapReduce 架构概述

> MapReduce 将计算过程分为两个阶段：Map 和 Reduce
>
> ① Map 阶段并行处理输入数据
>
> ② Reduce 阶段对 Map 结果进行汇总

#### 7、大数据生态体系

![大数据生态体系](https://shp-notes-1257820375.cos.ap-chengdu.myqcloud.com/shp-hadoop/%E5%A4%A7%E6%95%B0%E6%8D%AE%E6%8A%80%E6%9C%AF%E7%94%9F%E6%80%81%E4%BD%93%E7%B3%BB.png?q-sign-algorithm=sha1&q-ak=AKIDMdaImNPsQyFY1Wyji7gklhzPznStrxiD&q-sign-time=1561905423;1561909023&q-key-time=1561905423;1561909023&q-header-list=&q-url-param-list=&q-signature=6f457ff3ea0ede5559881ca238b08d715bad91ea&x-cos-security-token=882c51851a53b266d347fa480a8ca1d59ea8742f10001)

#### 8、hadoop 安装

**步骤：**

```
① 先拷贝 hadoop 的 tar 包（hadoop-2.7.2.tar.gz）至服务器指定目录下
假设把 hadoop-2.7.2.tar.gz 放在 『/usr/local/module』 目录下
② 将 tar 包解压，解压完成之后进入 hadoop 目录
cd hadoop-2.7.2
③ 获取 hadoop 的安装路径
pwd
『/usr/local/module/hadoop-2.7.2』
④ 编辑环境变量配置文件
vim /etc/profile
⑤ 配置 hadoop 环境变量
export HADOOP_HOME=/usr/local/module/hadoop-2.7.2
export PATH=$HADOOP_HOME/bin:$PATH
export PATH=$HADOOP_HOME/sbin:$PATH
⑥ 验证
使用 hadoop 命令，出现下面一大段描述字，表示环境变量配置成功
```

```shell
[root@hadoop1 hadoop-2.7.2]# hadoop

Usage: hadoop [--config confdir] [COMMAND | CLASSNAME]
  CLASSNAME            run the class named CLASSNAME
 or
  where COMMAND is one of:
  fs                   run a generic filesystem user client
  version              print the version
  jar <jar>            run a jar file
                       note: please use "yarn jar" to launch
                             YARN applications, not this command.
  checknative [-a|-h]  check native hadoop and compression libraries availability
  distcp <srcurl> <desturl> copy file or directories recursively
  archive -archiveName NAME -p <parent path> <src>* <dest> create a hadoop archive
  classpath            prints the class path needed to get the
  credential           interact with credential providers
                       Hadoop jar and the required libraries
  daemonlog            get/set the log level for each daemon
  trace                view and modify Hadoop tracing settings

Most commands print help when invoked w/o parameters.

```

**注意：**

> 在安装 hadoop 之前要配置主机名和 ip 的映射关系，否则在后面使用 hadoop 过程中会出现很多问题
>
> `vim /etc/hosts`
>
> 使用上面命令，配置好主机名和 ip 的映射关系

## 三、Hadoop 运行模式

Hadoop 运行模式包括，本地模式、伪分布式模式、完全分布式模式

#### 1、本地模式 grep 官方案例

```shell
mkdir input
cp etc/hadoop/*.xml input/
hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar grep input output 'dfs[a-z.]+'
cd output
cat part-r-00000
```

#### 2、本地模式 WordCount 官方案例

**步骤：**

① 在 hadoop 目录下创建一个 `wcinput` 文件夹

```shell
[root@hadoop1 hadoop-2.7.2]# mkdir wcinput
```

② 在 wcinput 文件夹下创建一个 wc.input 文件，并在里面编辑内容

````shell
vim wc.input

heping kevin James curry Jordan
heping
````

③ 回退到 hadoop 目录下执行程序

```shell
hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar wordcount wcinput/ wcoutput
```

④ 执行结果

```
[root@hadoop1 wcoutput]# cat part-r-00000 
James	1
Jordan	1
curry	1
heping	2
kevin	1
```

#### 3、伪分布式-启动 HDFS 并 运行 MR 程序

要想完成启动 HDFS 并运行 MR 程序，主要需要经过下面三个步骤：

> 1、配置集群
>
> 2、启动、测试集群增、删、查
>
> 3、执行 WordCount 案例

1）、配置集群

① 配置 `hadoop-env.sh`

> 在这个文件中主要是为了去修改 `JAVA_HOME` 
>
> ```shell
> echo $JAVA_HOME
> /usr/local/java/jdk1.8.0_144     # 先看下系统中 JAVA_HOME 的位置
>
> cd hadoop-2.7.2/etc/hadoop
> vim hadoop-env.sh
> 『
> export JAVA_HOME=${JAVA_HOME}
> # 把这里改成 export JAVA_HOME=/usr/local/java/jdk1.8.0_144 
> 』
> 然后保存退出
> ```
>
> 

② 配置 `core-site.xml`

> ```shell
> cd hadoop-2.7.2/etc/hadoop
> vim core-site.xml 
> 『
> configuration>
>         <!-- 指定HDFS中NameNode的地址 -->
>         <property>
>                 <name>fs.defaultFS</name>
>                  <value>hdfs://hadoop1:9000</value>
>         </property>
>
>         <!-- 指定Hadoop运行时产生文件的存储目录 -->
>         <property>
>                 <name>hadoop.tmp.dir</name>
>                 <value>/usr/local/module/hadoop-2.7.2/data/tmp</value>
>         </property>
> </configuration>
> 』
> ```
>
> 

③ 配置 `hdfs-site.xml`

> ```shell
> cd hadoop-2.7.2/etc/hadoop
> vim hdfs-site.xml
> 『
> <configuration>
>         <!-- 指定HDFS副本的数量 -->
>         <property>
>                 <name>dfs.replication</name>
>                 <value>1</value>
>         </property>
> </configuration>
> 』
> ```
>
> 

2）、启动集群

① 格式化 `NameNode` （第一次启动时需要格式化，以后就不需要了）

> ```shell
> cd hadoop-2.7.2/bin
> hdfs namenode -format      # 格式化 NameNode
> # 在格式化过程中，如果有任何提示，比如已经格式化过，是否重新格式化，这时候你就需要重新格式化
> ```

**注意：**

> 格式化 NameNode ，会产生新的集群 id，导致 NameNode 和 DataNode 的集群 id 不一致，集群找不到以往的数据。所以，格式化 NameNode 时，一定要先删除 data 数据和 log 日志，然后再格式化 NameNode（PS：格式化之前一定要先停止上次启动的所有 namenode 和 datanode 进程，然后再删除 data 和 log 数据）

② 启动 `NameNode`

> ```shell
> cd hadoop-2.7.2/sbin
> hadoop-daemon.sh start namenode    # 启动 NameNode
> jps
> 9233 NameNode      # 证明启动成功
> 9321 Jps
> ```
>
> 

③ 启动 `DataNode`

> ```shell
> cd hadoop-2.7.2/sbin
> hadoop-daemon.sh start datanode      # 启动 DataNode
> jps
> 9233 NameNode
> 9540 Jps
> 9469 DataNode     # 证明启动成功
> ```
>
> 

3）、查看集群

① 查看是否启动成功

> ```shell
> jps
> 9233 NameNode
> 9540 Jps
> 9469 DataNode     # 证明启动成功
> ```
>
> 

② web 端查看 HDFS 文件系统

> `http://192.168.148.141:50070`

4）、操作集群

① 在 HDFS 文件系统上创建一个 input 文件夹

> `./bin/hdfs dfs -mkdir -p /usr/heping/input`

② 将测试文件内容上次到文件系统上

> `./bin/hdfs dfs -put wcinput/wc.input /user/heping/input`
>
> 第一个路径是测试文件在本地的路径，第二个路径是 HDFS 文件系统上的路径

③ 运行 MapReduce 程序，执行 WordCount 案例

> `./bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar wordcount /user/heping/input/ /user/heping/output`
>
> 前后两个输入和输出的路径都是 HDFS 文件系统上的路径

④ 查看输出结果

> `./bin/hdfs dfs -cat /user/heping/output/p*`
> James	1
> Jordan	1
> curry	1
> heping	2
> kevin	1

DataNode 和 NameNode 进程同时只能有一个工作的问题分析：

![DataNode 和 NameNode问题分析](https://shp-notes-1257820375.cos.ap-chengdu.myqcloud.com/shp-hadoop/DataNode%E5%92%8CNameNode%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90.png?q-sign-algorithm=sha1&q-ak=AKIDY4ec1O3DSZtWqNFGx2voSAjJbpWGViUE&q-sign-time=1562505102;1562508702&q-key-time=1562505102;1562508702&q-header-list=&q-url-param-list=&q-signature=17e2c31f9c69751087ecb859f94ee7b2f4120f77&x-cos-security-token=c01cb0f51a31f23e3fa28e6cb6f045513fe8368810001)

#### 4、启动 YARN 并运行 MR 程序

要想完成启动 YARN 并运行 MR 程序，需要经过下面几个步骤：

> - 配置集群
> - 启动测试集群增、删、查
> - 在 YARN 上执行 WordCount 案例

1）、配置集群

① 配置 `yarn-env.sh`

```shell
echo $JAVA_HOME
/usr/local/java/jdk1.8.0_144     # 先看下系统中 JAVA_HOME 的位置

cd hadoop-2.7.2/etc/hadoop
vim yarn-env.sh
『
export JAVA_HOME=xxxxxxxxx
# 把这里改成 export JAVA_HOME=/usr/local/java/jdk1.8.0_144 
』
然后保存退出
```

② 配置 `yarn-site.xml` 

```Xml
cd hadoop-2.7.2/etc/hadoop
vim yarn-site.xml	
『
<configuration>
<!-- Site specific YARN configuration properties -->
        <!-- Reducer获取数据的方式 -->
        <property>
                <name>yarn.nodemanager.aux-services</name>
                <value>mapreduce_shuffle</value>
        </property>

        <!-- 指定YARN的ResourceManager的地址 -->
        <property>
                <name>yarn.resourcemanager.hostname</name>
                <value>hadoop1</value>
        </property>
</configuration>

』
```

③ 配置 `mapred-env.sh`

```shell
echo $JAVA_HOME
/usr/local/java/jdk1.8.0_144     # 先看下系统中 JAVA_HOME 的位置

cd hadoop-2.7.2/etc/hadoop
vim mapred-env.sh
『
# export JAVA_HOME=/home/y/libexec/jdk1.6.0/
# 把这里改成 export JAVA_HOME=/usr/local/java/jdk1.8.0_144 
』
然后保存退出
```

④ 将 `mapred-site.xml.template` 重命名为 `mapred-site.xml`

```shell
cd hadoop-2.7.2/etc/hadoop
mv mapred-site.xml.template mapred-site.xml
vim  mapred-site.xml
『
<configuration>
        <!-- 指定MR运行在YARN上 -->
        <property>
                <name>mapreduce.framework.name</name>
                <value>yarn</value>
        </property>
</configuration>
』
保存退出
```

2）、启动集群

① 启动前必须保证 NameNode 和 DataNode 已经启动

② 启动 ResourceManager 

```shell
cd hadoop-2.7.2/sbin
yarn-daemon.sh start resourcemanager  # 启动 ResourceManager
[root@hadoop1 sbin]# jps
6387 Jps
5638 NameNode
5757 DataNode
6174 ResourceManager    # 证明启动成功
```

③ 启动 NodeManager

```shell
cd hadoop-2.7.2/sbin
yarn-daemon.sh start nodemanager  # 启动 NodeManager
[root@hadoop1 sbin]# jps
5638 NameNode
6471 NodeManager    # 证明启动成功
6552 Jps
5757 DataNode
6174 ResourceManager
```

3）、查看集群

在浏览器查看 YARN ：

> `http://192.168.148.141:8088`

4）、操作集群

① 删除文件系统上的 output 文件夹

> cd hadoop-2.7.2/bin
>
> `hdfs dfs -rm -r /user/heping/output`

② 运行 MapReduce 程序，执行 WordCount 案例

> `bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar wordcount /user/heping/input/ /user/heping/output`
>
> 前后两个输入输出路径都是 hdfs 文件系统上的路径

③ 查看运行结果

> `bin/hdfs dfs -cat /user/heping/output/p*`
> James	1
> Jordan	1
> curry	1
> heping	2
> kevin	1

#### 5、配置历史服务器

为了查看程序的历史运行情况，需要配置一下历史服务器。

1）、配置 `mapred-site.xml`

```xml
cd hadoop-2.7.2/etc/hadoop
vim mapred-site.xml	
『
<configuration>
        <!-- 历史服务器端地址 -->
        <property>
                <name>mapreduce.jobhistory.address</name>
                <value>hadoop1:10020</value>
        </property>
        <!-- 历史服务器web端地址 -->
        <property>
                <name>mapreduce.jobhistory.webapp.address</name>
                <value>hadoop1:19888</value>
        </property>
</configuration>
』
```

2）、启动历史服务器

```shell
cd hadoop-2.7.2/sbin
mr-jobhistory-daemon.sh start historyserver
```

3）、查看历史服务器是否启动

```shell
jps
4740 NodeManager
4965 JobHistoryServer    # 证明历史服务器启动了
4485 ResourceManager
5001 Jps
4202 NameNode
4300 DataNode
```

4）、web 端查看 JobHistory

> `http://192.168.148.141:19888`

#### 6、配置日志聚集

日志聚集概念：应用运行完成以后，将程序运行日志信息上传到 HDFS 系统上。

**注意：**

> 开启日志聚集功能，需要重新启动 `NodeManager` 、`ResourceManager` 和 `HistoryManager` 

具体步骤：

1）、配置  `yarn-site.xml` 

```shell
cd /hadoop-2.7.2/etc
vim yarn-site.xml
『
<configuration>
        <!-- 日志聚集功能使能 -->
        <property>
                <name>yarn.log-aggregation-enable</name>
                <value>true</value>
        </property>
        <!-- 日志保留时间设置7天 -->
        <property>
                <name>yarn.log-aggregation.retain-seconds</name>
                <value>604800</value>
        </property>
</configuration>
』
```

2）、关闭 NodeManager 、ResourceManager、HistoryManager

```shell
cd hadoop-2.7.2/sbin
yarn-daemon.sh stop nodemanager    # 关闭 NodeManager
yarn-daemon.sh stop resourcemanager  # 关闭 ResourceManager
mr-jobhistory-daemon.sh stop historyserver   # 关闭 Historyserver
jps
7321 Jps
4202 NameNode
4300 DataNode
```

3）、启动 NodeManager 、ResourceManager、HistoryManager

```shell
cd hadoop-2.7.2/sbin
yarn-daemon.sh start nodemanager    # 启动 NodeManager
yarn-daemon.sh start resourcemanager  # 启动 ResourceManager
mr-jobhistory-daemon.sh start historyserver   # 启动 Historyserver
```

4）、删除 hdfs 上已经存在的文件输出目录

```shell
cd hadoop-2.7.2/bin
hdfs dfs -rm -f /user/heping/output
```

5）、执行 wordCount 程序

```shell
cd hadoop-2.7.2
hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.2.jar wordcount /user/heping/input /user/heping/output
```

6）、查看日志

```shell
http://192.168.148.141:19888
```

7、集群分发脚本

```bash
#!/bin/bash
#1 获取输入参数个数，如果没有参数，直接退出
pcount=$#
if((pcount==0)); then
echo no args;
exit;
fi

#2 获取文件名称
p1=$1
fname=`basename $p1`
echo fname=$fname

#3 获取上级目录到绝对路径
pdir=`cd -P $(dirname $p1); pwd`
echo pdir=$pdir

#4 获取当前用户名称
user=`whoami`

#5 循环
for((host=142; host<144; host++)); do
        echo ------------------- hadoop$host --------------
        rsync -rvl $pdir/$fname $user@192.168.148.$host:$pdir
done
```

#### 7、集群配置

1）、集群部署规划

|      | 192.168.148.141        | 192.168.148.142                  | 192.168.148.143                 |
| ---- | ---------------------- | -------------------------------- | ------------------------------- |
| HDFS | NameNode<br />DataNode | DataNode                         | SecondaryNameNode<br />DataNode |
| YARN | NodeManager            | ResourceManager<br />NodeManager | NodeManager                     |

上面表格说明：

> 首先有三台服务器（141、142、143），在这三台服务器上我们要去配置  HDFS 和 YARN。首先看 HDFS ，它包括 NameNode、DataNode、SecondaryNameNode ，其次你要知道 NameNode 和 SecondaryNameNode 它们的内存占比基本上就是 1:1 。比如说你服务器内存 128G ，你如果把 NameNode 和 SecondaryNameNode 配置在一台机器上，那么它们各自只能占 64G，这样就会严重影响集群性能。所以应该把这两个放在不同的机器上。再来看 YARN 的配置，YARN 包括 NodeManager 和 ResourceManager 。这个 ResourceManger 是整个集群资源的老大，它也非常占用内存，所以不能和 NameNode、SecondaryNameNode 在一台机器上。

2）、集群配置步骤

PS：下面所有的配置都在一台机器上配置好，然后通过集群分发脚本将所有配置同步到另外两台机器上

① 核心配置文件

配置 `core-site.xml`

```xml
vim hadoop-2.7.2/etc/hadoop/core-site.xml
<configuration>
        <!-- 指定HDFS中NameNode的地址 -->
        <property>
                <name>fs.defaultFS</name>
                 <value>hdfs://192.168.148.141:9000</value>
        </property>

        <!-- 指定Hadoop运行时产生文件的存储目录 -->
        <property>
                <name>hadoop.tmp.dir</name>
                <value>/usr/local/module/hadoop-2.7.2/data/tmp</value>
        </property>
</configuration>
```

② HDFS 的配置文件

配置 `hadoop-env.sh`

```bash
vim hadoop-2.7.2/etc/hadoop/hadoop-env.sh
export JAVA_HOME=/usr/local/java/jdk1.8.0_144
```

配置 `hdfs-site.xml`

```xml
vim hadoop-2.7.2/etc/hadoop/hdfs-site.xml
<configuration>
        <!-- 指定HDFS副本的数量 -->
        <property>
                <name>dfs.replication</name>
                <value>3</value>
        </property>
        <!-- 指定Hadoop辅助名称节点主机配置 -->
        <property>
                <name>dfs.namenode.secondary.http-address</name>
                 <value>192.168.148.143:50090</value>
        </property>
</configuration>
```

③ YARN 的配置文件

配置 `yarn-env.sh`

```bash
vim hadoop-2.7.2/etc/hadoop/yarn-env.sh
export JAVA_HOME=/usr/local/java/jdk1.8.0_144
```

配置 `yarn-site.xml`

```xml
vim hadoop-2.7.2/etc/hadoop/yarn-site.xml
<configuration>
<!-- Site specific YARN configuration properties -->
        <!-- Reducer获取数据的方式 -->
        <property>
                <name>yarn.nodemanager.aux-services</name>
                <value>mapreduce_shuffle</value>
        </property>

        <!-- 指定YARN的ResourceManager的地址 -->
        <property>
                <name>yarn.resourcemanager.hostname</name>
                <value>192.168.148.142</value>
        </property>
        <!-- 日志聚集功能使能 -->
        <property>
                <name>yarn.log-aggregation-enable</name>
                <value>true</value>
        </property>
        <!-- 日志保留时间设置7天 -->
        <property>
                <name>yarn.log-aggregation.retain-seconds</name>
                <value>604800</value>
        </property>
</configuration>

```

④ MapReduce 配置文件

配置 `mapred-env.sh`

```bash
vim hadoop-2.7.2/etc/hadoop/mapred-env.sh
export JAVA_HOME=/usr/local/java/jdk1.8.0_144
```

配置 `mapred-site.xml`

```xml
vim hadoop-2.7.2/etc/hadoop/mapred-site.xml
<configuration>
        <!-- 指定MR运行在YARN上 -->
        <property>
                <name>mapreduce.framework.name</name>
                <value>yarn</value>
        </property>
        <!-- 历史服务器端地址 -->
        <property>
                <name>mapreduce.jobhistory.address</name>
                <value>192.168.148.141:10020</value>
        </property>
        <!-- 历史服务器web端地址 -->
        <property>
                <name>mapreduce.jobhistory.webapp.address</name>
                <value>192.168.148.141:19888</value>
        </property>
</configuration>
```

以上是集群中一台服务器节点的配置，配置完成后就可以使用集群分发脚本将配置同步到另外两台机器上。

#### 8、集群单节点启动

1）、如果集群是第一次启动，需要格式化 NameNode

注意：

格式化 NameNode 时，一定要先删除 data 数据和 log 日志

```shell
cd hadoop-2.7.2/bin
hdfs namenode -format      # 格式化 NameNode
```

2）、在 192.168.148.141 上启动 NameNode 和 DataNode

```shell
cd hadoop-2.7.2/sbin
./hadoop-daemon.sh start namenode   # 启动 namenode
./hadoop-daemon.sh start datanode   # 启动 datanode
[root@hadoop1 sbin]# jps
7893 NameNode
8008 DataNode
8107 Jps
```

3）、在 192.168.148.142 上启动 DataNode

```shell
cd hadoop-2.7.2/sbin
./hadoop-daemon.sh start datanode   # 启动 datanode
[root@hadoop2 sbin]# jps
8035 DataNode
8119 Jps
```

4）、在 192.168.148.143 上启动 DataNode

```shell
cd hadoop-2.7.2/sbin
./hadoop-daemon.sh start datanode   # 启动 datanode
[root@hadoop3 sbin]# jps
6112 Jps
6077 DataNode
```

**思考：**

如果我每次都是一个一个节点启动，如果节点数增加到 1000 个怎么办？

#### 9、集群 ssh 配置

1）、ssh 免密登录原理

![ssh免密登录原理](https://shp-notes-1257820375.cos.ap-chengdu.myqcloud.com/shp-hadoop/ssh%E5%85%8D%E5%AF%86%E7%99%BB%E5%BD%95%E5%8E%9F%E7%90%86.png?q-sign-algorithm=sha1&q-ak=AKID3i5rIVmNuulYgI3dTi7FXIoW8lcogEUH&q-sign-time=1563116545;1563120145&q-key-time=1563116545;1563120145&q-header-list=&q-url-param-list=&q-signature=182c626de3b2a6cf4e281ea2faeb0db763111183&x-cos-security-token=ce9cc00c31cdd2b5d019e935c23a84b08aa110f410001)

2）、生成公钥和私钥

```shell
首先进入到当前用户的家目录
cd ~
ls -la     # 这个命令可以看到在当前目录下有一个 .ssh 的文件夹
cd .ssh
ssh-keygen -t rsa   # 生成对应的公钥和私钥
# -t rsa 表示使用 rsa 加密算法
# 上面的命令输入完成之后，敲三个回车就会生成两个文件 id_rsa(私钥)    id_rsa.pub(公钥)
ll
-rw-------. 1 root root 1675 7月  14 23:15 id_rsa
-rw-r--r--. 1 root root  394 7月  14 23:15 id_rsa.pub
-rw-r--r--. 1 root root  397 7月  14 22:37 known_hosts
```

3）、将公钥拷贝到要免密登录的目标机器上

```shell
# 我现在需要把公钥拷贝到 192.168.148.142 和 192.168.148.143 这两台机器上
# 当前机器是 192.168.148.141
pwd
/root/.ssh    # 当前用户家目录的 .ssh 文件夹下
ssh-copy-id 192.168.148.141      # 自己这台机器也配置下，不然使用 ssh 自己登录自己也需要输入密码  
ssh-copy-id 192.168.148.142
ssh-copy-id 192.168.148.143

# 现在我去 192.168.148.142 这台机器的 『/root/.ssh』 目录下
[root@hadoop2 .ssh]# ll
总用量 8
-rw-------. 1 root root 394 7月  14 23:30 authorized_keys  # 会生成一个这个文件，这个文件的内容就是 192.168.148.141 机器的公钥 
-rw-r--r--. 1 root root 397 7月  14 22:37 known_hosts

```

上面的步骤展示了使用公钥和私钥实现免密登录到目标机器上，总结一下：

> 比如说我当前机器是 141 ，然后我想通过 ssh 免密登录到 142 和 143 的机器上，那么我的做法就是，先在 141 机器上生成一对公钥和私钥，然后把公钥拷贝到 142 和 143 机器上，这样就实现了 ssh 免密登录。拷贝后，142 和 143 机器都会生成一个 authorized_keys 文件，里面是 141 的公钥，141 想免密登录 142 和 143 都是通过这个文件来实现的。
>
> 那么假如我现在所在机器是 142，我想免密登录 141 和 143 ，你发现是不行的。那么做法就是现在 142 上生成一对公钥和私钥，然后把 142 的公钥拷贝到 141 和 143 上，这样才能实现免密登录。

上面我们配置免密登录时因为 192.168.148.141 上有 NameNode ，它需要和 142、143 进行通信，需要免密登录。同时 192.168.148.142 上有 ResourceManager 它也需要和另外两台机器进行通信，所以也需要免密登录，配置方式和上述步骤类似。

#### 10、集群群起

上面之所以要配置一下 ssh 其实是为我们群起集群服务的。

1）、配置 slaves 

```shell
cd hadoop-2.7.2/etc/hadoop
vim slaves           # 首先删除里面自带的 localhost
192.168.148.141      # 把 datanode 所在的节点都配置在这里
192.168.148.142
192.168.148.143
```

**注意：**

> slaves 这个文件开头和结尾不允许有空格，文件中也不允许有空行

上面的配置只是在一台服务器节点上配置，配置好之后我们就可以使用集群分发脚本同步到另外两台机器上。

2）、启动集群

①如果集群是第一次启动需要格式化 NameNode（格式化之前一定要先停止上次启动的所有 NameNode 和 DataNode 进程，然后再删除 data 和 log 数据）

> 格式化 namenode 命令前面有说过
>

② 启动 HDFS

```shell
cd hadoop-2.7.2/sbin
./start-dfs.sh
jps
4660 NameNode
7878 Jps
4794 DataNode

# 这样三台机器上的 namenode 和 datanode secondarynamenode 都会被启动起来
```

③ 启动 YARN

```shell
cd hadoop-2.7.2/sbin
./start-yarn.sh
```

**注意：**

> NameNode 和 ResourceManager 如果不是在同一台机器，不能在 NameNode 上启动 YARN，应该在 ResourceManager 上启动 YARN

#### 11、集群文件存储路径说明

我们可以使用命令向 hdfs 中上传一个文件，如：

> `bin/hdfs dfs -put ../hadoop-2.7.2.tar.gz /`

这个命令表示我把 `hadoop-2.7.2.tar.gz` 这个文件上传到 hdfs 的根目录下，但是这个文件具体的位置在哪？

> 首先我们知道他肯定是在 Linux 服务器中，但是具体位置在哪？
>
> 答：数据一般保存在我们配置的 `data` 目录下，所以我们去 data 目录下找
>
> `/usr/local/module/hadoop-2.7.2/data/tmp/dfs/data/current/BP-372575800-192.168.148.141-1563113976815/current/finalized/subdir0/subdir0`   最后在这个目录下找到我们需要的文件。（可能一个大文件它会分成好几块来存，找到后把他们拼接在一起就可以得到一个完整的文件）

#### 12、集群启动停止方式总结

1）、各个服务组件逐一启动停止

> ① 分别启动/停止 HDFS 组件
>
> `hadoop-daemon.sh start/stop  namenode/datanode/secondarynamenode`
>
> ② 启动/停止 YARN
>
> `yarn-daemon.sh start/stop resourcemanager/nodemanager`

2）、整体启动（配置 SSH 是前提）

> ① 整体启动/停止 HDFS
>
> `start-dfs.sh     stop-dfs.sh`
>
> ② 整体启动/停止 YARN
>
> start-yarn.sh          stop-yarn.sh

#### 13、crontab 定时任务调度

1）、重新启动 crond 服务

> `service crond restart`

2）、基本语法

> `crontab [选项]`
>
> 选项：
>
> ​	`-e` ： 编辑 crontab 定时任务
>
> ​	`-l` ：查询 crontab 任务
>
> ​	`-r` ：删除当前用户所有的 crontab 任务

3）、使用

`* * * * * 执行的任务`

| 项目         | 含义                 | 范围                       |
| ------------ | -------------------- | -------------------------- |
| `第一个 "*"` | 一小时当中的第几分钟 | 0-59                       |
| `第二个 "*"` | 一天当中的第几小时   | 0-23                       |
| `第三个 "*"` | 一个月当中的第几天   | 1-31                       |
| `第四个 "*"` | 一年当中的第几个月   | 1-12                       |
| `第五个 "*"` | 一周当中的星期几     | 0-7（0 和 7 都代表星期日） |

 4）、特殊符号

| 特殊符号 | 含义                                                         |
| -------- | ------------------------------------------------------------ |
| `*`      | 代表任何时间。比如第一个时间就代表一小时中每分钟都执行一次   |
| `,`      | 代表不连续的时间。比如 `"0 8,12,16 * * *"`  就代表在每天的 8 点 0 分，12 点 0 分，16 点 0 分都执行一次命令 |
| `-`      | 代表连续的时间范围。比如 `"0 5 * * 1-6"`  ,代表在周一到周六凌晨 5 点 0 分执行命令 |
| `        | 代表每隔多久执行一次。比如 `"*/10 * * * *"` 代表每隔 10 分钟就执行一遍命令 |

#### 14、集群时间同步

**先说集群时间为什么要进行同步？**

> 比如说我现在有三台服务器，假如说这三台机器时间不一致，就可能出现问题。我在这三台服务器上部署了集群，现在要在一点钟执行一个任务，但是这是哪个机器的时间都不一样，这样就出问题了。

**时间同步方式：**

> 找一个机器作为时间服务器，所有的机器与这台机器的时间进行定时的同步，比如：每隔十分钟，同步一次时间。

**配置时间同步步骤：**

1）、时间服务器配置（必须是 root 用户）

① 检查 ntp 是否安装

```shell
[root@hadoop1 桌面]# rpm -qa |grep ntp
fontpackages-filesystem-1.41-1.1.el6.noarch       # 出现下面三行，证明安装
ntpdate-4.2.6p5-10.el6.centos.x86_64
ntp-4.2.6p5-10.el6.centos.x86_64
```

② 修改 ntp 配置文件

> `vim /etc/ntp.conf`

修改内容：

a）、授权 `192.168.1.0-192.168.1.255` 网段上所有机器可以从这条机器上查询和同步时间

> 表现在配置文件中的操作就是：
>
> ```shell
> # Hosts on local network are less restricted.
> restrict 192.168.1.0 mask 255.255.255.0 nomodify notrap    #把这行注释打开
>          192.168.148.0      # 把这里的网段改成 148 网段
> ----------------------------------------------------------------------------
> 即：
> restrict 192.168.148.0  mask 255.255.255.0 nomodify notrap 
> ```
>
> **注意：**
>
> 把原来配置文件中注释行打开后，它的网络 ip 是 `192.168.1.0`   这里需要根据你机器具体的 ip 网段修改下，比如说我机器集群的网段都在 `192.168.148.x`  那么我就把这里改成 `192.168.148.0`  开始

b）、集群在局域网中，不使用其他互联网上的时间

> 表现在配置文件中的操作就是：
>
> ```shell
> # Use public servers from the pool.ntp.org project.
> # Please consider joining the pool (http://www.pool.ntp.org/join.html).
> server 0.centos.pool.ntp.org iburst
> server 1.centos.pool.ntp.org iburst      # 需要把这四行全部注释掉
> server 2.centos.pool.ntp.org iburst
> server 3.centos.pool.ntp.org iburst
> ----------------------------------------------------------------------------
> 即：
> #server 0.centos.pool.ntp.org iburst
> #server 1.centos.pool.ntp.org iburst      
> #server 2.centos.pool.ntp.org iburst
> #server 3.centos.pool.ntp.org iburst
> ```
>
> 

c）、当该节点丢失网络连接，依然可以采用本地时间作为时间服务器为集群中其他节点提供时间同步

> ```shell
> server 127.127.1.0
> fudge 127.127.1.0 stratum 10      # 把这两行直接粘贴到配置文件最后即可
> ```
>
> 

③ 修改 `/etc/sysconfig/ntpd`

> ```shell
> # 添加如下内容
> SYNC_HWCLOCK=yes       # 让硬件时间与系统时间一起同步
> ```
>
> 其实就是读取硬件的时钟信息

④ 重新启动 ntpd 服务

> `service htpd restart`
>
> ```shell
> [root@hadoop1 桌面]# service ntpd status
> ntpd (pid  7758) 正在运行...     # 证明 ntpd 正在运行
> ```
>
> 

⑤ 设置 ntpd 服务开机启动

> `chkconfig ntpd on`        

2）、其他机器配置（必须 root 用户）

① 在其他机器配置 10 分钟与时间服务器同步一次

> `crontab -e`
>
> 编写的定时任务如下：
>
> ```
> */10 * * * * /usr/sbin/ntpdate 192.168.148.141
> ```
>
> 

## 四、HDFS

### HDFS 概述

#### 1、HDFS 产生背景

随着数据量越来越大，在一个操作系统存不下所有的数据，那么就分配到更多操作系统分配的磁盘中，但是不方便管理和维护，迫切需要一种系统来管理多台机器上的文件，这就是分布式文件管理系统。HDFS 只是分布式文件管理系统中的一种。

#### 2、HDFS 定义

HDFS（Hadoop Distributed File System）它是一个文件系统，用于存储文件，通过目录树来定位文件。其次，它是分布式的，由很多服务器联合起来实现其功能，集群中的服务器有各自的角色。

**HDFS 使用场景：**

> 适合一次写入，多次读出的场景，且不支持文件的修改。适合用来做数据分析，并不适合用来做网盘应用（网盘涉及到增删改查）。

#### 3、HDFS 优缺点

**优点：**

> 1）、高容错性
>
> ① 数据自动保存多个副本。它通过增加副本的形式，提高容错性。
>
> ②某一个副本丢失以后，它可以自动恢复
>
> 2）、适合处理大数据
>
> ①数据规模：能够处理数据规模达到 GB、TB、甚至 PB 级别的数据
>
> ② 文件规模：能够处理百万规模以上的文件数量，数量相当之大
>
> 3）、可构建在廉价机器上，通过多副本机制，提高可靠性

**缺点：**

> 1）、不适合低延时数据访问，比如毫秒级的存储数据，是做不到的
>
> 2）、无法高效的对大量小文件进行存储
>
> ①存储大量小文件的话，它会占用 NameNode 大量的内存来存储文件目录和块信息。这样是不可取的，因为 NameNode 的内存总是有限的（比如说几百万个小文件需要存储，那么 NameNode 就需要把这几百万个小文件的文件目录和块信息都存下来，内存很快就耗完了）
>
> ② 小文件存储的寻址时间会超过读取时间，它违反了 HDFS 的设计目标
>
> 3）、不支持并发写入、文件随机修改
>
> ① 一个文件只能有一个线程写，不允许多个线程同时写
>
> ② 仅支持数据 append（追加），不支持文件的随机修改

#### 4、HDFS 组成架构

![hdfs架构图](https://shp-notes-1257820375.cos.ap-chengdu.myqcloud.com/shp-hadoop/hdfs%E6%9E%B6%E6%9E%84%E5%9B%BE.png?q-sign-algorithm=sha1&q-ak=AKIDWlm5niwkCvw9aNY6y2xp0PmJlrXqkM8w&q-sign-time=1563455506;1563459106&q-key-time=1563455506;1563459106&q-header-list=&q-url-param-list=&q-signature=54ae2ff2ddf8a197e00b72961aa56a25f56fed79&x-cos-security-token=a2ac32073e70418ea238651590546ffd3f7a34f610001)



**NameNode（nn）：**

> NameNode（nn）：就是 Master，它是一个主管、管理者
>
> - 管理 HDFS 的名称空间
> - 配置副本策略
> - 管理数据块（Block）映射信息
> - 处理客户端读写请求

**DataNode（dn）：**

> DataNode（dn）：就是 Slave，NameNode 下达命令，DataNode 执行实际的操作
>
> - 存储实际的数据块
> - 执行数据库的读/写操作

**Secondary NameNode（snn）：**

> Secondary NameNode：并非 NameNode 的热备。当 NameNode 挂掉的时候，它并不能马上替换 NameNode 并提供服务。
>
> - 辅助 NameNode,分担其工作量，比如 定期合并 Fsimage 和 Edits ，并推送给 NameNode
> - 在紧急情况下，可辅助恢复 NameNode

**Client：**

> 就是客户端
>
> - 文件切分。文件上传 HDFS 的时候，Client 将文件切分成一个一个的 Block，然后进行上传
> - 与 NameNode 交互，获取文件的位置信息
> - 与 DataNode 交互，读取或者写入数据
> - Client 提供一些命令来管理 HDFS，比如 NameNode 格式化
> - Client 可以通过一些命令来访问 HDFS，比如对 HDFS 增删改查操作

#### 5、HDFS 块的大小设置

HDFS 中的文件在物理上是分块存储（Block），块的大小可以通过配置参数（dfs.blocksize）来规定，默认大小在 Hadoop2.x 版本中是 128M ，老版本（Hadoop1.x）是 64M

> ①HDFS 中的文件存在一个一个的 block 上
>
> ② 我想往 block 里面写东西，寻址时间约为 10ms，即查找到目标 block 的时间为 10ms
>
> ③ **寻址时间为传输时间的 1% 时，为最佳状态。** 因此，传输时间 ：10ms/0.01=1000ms=1s
>
> ④ 目前磁盘的传输速率普遍为 100MB/s 
>
> ⑤ block 大小： 1s * 100MB/s = 100MB       约为 100MB 左右

**为什么块的大小不能设置太小，也不能设置太大？**

> - HDFS 的块设置太小，会增加寻址时间，程序一直在找块的开始位置
>   - 比如说你有几百万个块，那么我想找到其中一个块往里面写寻址时间就会很长
> - 如果块设置的太大，从**磁盘传输数据的时间**会明显**大于定位这个块开始位置所需时间**。导致程序在处理这块数据时，会非常慢

**总结：**

==HDFS 块的大小设置主要取决于磁盘的传输速率==

#### **6、HDFS 相关 shell命令**

1）、基本语法

> `bin/hadoop fs 具体命令`       或者      `bin/hdfs dfs 具体命令`
>
> dfs 是 fs 的实现类

2）、常用命令

① 先需要启动 hadoop 集群

> ```shell
> [root@hadoop1 sbin]# pwd
> /usr/local/module/hadoop-2.7.2/sbin
> [root@hadoop1 sbin]# ./start-dfs.sh
> -------------------------------------
> [root@hadoop2 sbin]# pwd
> /usr/local/module/hadoop-2.7.2/sbin
> [root@hadoop2 sbin]# ./start-yarn.sh
> ```
>
> 

② `-help`

> 显示这个命令的帮助信息 

```shell
[root@hadoop1 bin]# hadoop fs -help rm
-rm [-f] [-r|-R] [-skipTrash] <src> ... :
  Delete all files that match the specified file pattern. Equivalent to the Unix
  command "rm <src>"
                                                                                 
  -skipTrash  option bypasses trash, if enabled, and immediately deletes <src>   
  -f          If the file does not exist, do not display a diagnostic message or 
              modify the exit status to reflect an error.                        
  -[rR]       Recursively deletes directories 
```

③ `-ls`

> 显示目录信息 

```shell
[root@hadoop1 bin]# hadoop fs -ls /
Found 2 items
-rw-r--r--   3 root supergroup  197657687 2019-07-16 19:27 /hadoop-2.7.2.tar.gz
drwxr-xr-x   - root supergroup          0 2019-07-16 19:26 /wcinput
```

④ `-mkdir`

> 在 HDFS 上创建目录

```shell
[root@hadoop1 bin]# hadoop fs -mkdir -p /shp/heping/shuai
[root@hadoop1 bin]# hadoop fs -ls -R /shp
drwxr-xr-x   - root supergroup          0 2019-07-22 23:07 /shp/heping
drwxr-xr-x   - root supergroup          0 2019-07-22 23:07 /shp/heping/shuai
```

⑤ `-moveFromLocal`

> 从本地剪切粘贴到 HDFS

```shell
# 第一个路径是本地文件路径，第二个是 hdfs 文件路径
[root@hadoop1 bin]# hadoop fs -moveFromLocal ./shp.txt /shp/heping/shuai
[root@hadoop1 bin]# hadoop fs -ls /shp/heping/shuai
Found 1 items
-rw-r--r--   3 root supergroup          6 2019-07-22 23:14 /shp/heping/shuai/shp.txt

# 同时你会发现本地的 shp.txt 没有了，被剪切掉了
```

⑥ `-appendToFile`

> 追加一个文件到已经存在的文件末尾

```shell
# 第一个路径是本地文件路径，第二个是 hdfs 文件路径
[root@hadoop1 bin]# hadoop fs -appendToFile heping.txt /shp/heping/shuai/shp.txt
```

⑦ `-cat`

> 显示文件内容

```shell
[root@hadoop1 bin]# hadoop fs -cat /shp/heping/shuai/shp.txt
hello
```

⑧ `-chgrp 、 -chmod 、-chown` 

> 修改文件所属权限，和 Linux 中用法一样
>

```shell
[root@hadoop1 bin]# hadoop fs -ls -h /shp/
Found 1 items
drwxr-xr-x   - root supergroup          0 2019-07-22 23:07 /shp/heping
[root@hadoop1 bin]# hadoop fs -chgrp -R root /shp/heping
[root@hadoop1 bin]# hadoop fs -ls -h /shp/
Found 1 items
drwxr-xr-x   - root root          0 2019-07-22 23:07 /shp/heping
```

⑨ `-copyFromLocal`

> 从本地文件系统中拷贝文件到 HDFS 中

```shell
# 第一个路径是本地文件路径，第二个路径是 hdfs 上路径
[root@hadoop1 bin]# hadoop fs -copyFromLocal ./hello.txt /shp/heping/shuai
[root@hadoop1 bin]# hadoop fs -ls /shp/heping/shuai
Found 2 items
-rw-r--r--   3 root root          3 2019-07-22 23:41 /shp/heping/shuai/hello.txt
-rw-r--r--   3 root root          6 2019-07-22 23:26 /shp/heping/shuai/shp.txt

# 同时你会发现本地的 hello.txt 还存在
```

⑩ `-copyToLocal`

> 从 HDFS 拷贝到本地

```shell
# 第一个参数是 hdfs 中的路径,第二个参数是本地路径
[root@hadoop1 bin]# hadoop fs -copyToLocal /shp/heping/shuai/shp.txt ./
```

11 `-cp`

> 从 HDFS 的一个路径拷贝到 HDFS 的另一个路径

```shell
[root@hadoop1 bin]# hadoop fs -cp /shp/heping/shuai/shp.txt /shp/heping
[root@hadoop1 bin]# hadoop fs -ls /shp/heping
Found 2 items
-rw-r--r--   3 root root          6 2019-07-22 23:54 /shp/heping/shp.txt
drwxr-xr-x   - root root          0 2019-07-22 23:41 /shp/heping/shuai
```

12 `-mv`

> 在 HDFS 目录中移动文件
>

```shell
[root@hadoop1 bin]# hadoop fs -mv /shp/heping/shp.txt /
[root@hadoop1 bin]# hadoop fs -ls /
Found 4 items
-rw-r--r--   3 root supergroup  197657687 2019-07-16 19:27 /hadoop-2.7.2.tar.gz
drwxr-xr-x   - root supergroup          0 2019-07-22 23:07 /shp
-rw-r--r--   3 root root                6 2019-07-22 23:54 /shp.txt
drwxr-xr-x   - root supergroup          0 2019-07-16 19:26 /wcinput
```

13 `-get`

> 等同于 copyToLocal   就是从 hdfs 下载文件到本地

```shell
# 第一个参数是 hdfs 中的路径,第二个参数是本地路径
[root@hadoop1 bin]# hadoop fs -get /shp.txt ./
```

14 `-getmerge`

> 合并下载多个文件，比如 hdfs 的目录 /shp 目录下有多个文件，那么我就可以把这几个文件合并在一起下载下来

```shell
# 前面的路径是 hdfs 上文件路径，后面是本地文件路径
[root@hadoop1 bin]# hadoop fs -getmerge /heping.txt /shp.txt ./merge.txt
```

15 `-put`

> 等同于 copyFromLocal

```shell
# 第一个路径是本地文件路径，第二个是 hdfs 文件路径
[root@hadoop1 bin]# hadoop fs -put ./heping.txt /
```

16 `-tail`

> 显示文件末尾

```shell
[root@hadoop1 bin]# hadoop fs -tail /shp.txt
hello
```

17 `-rm`

> 删除文件或文件夹

```shell
[root@hadoop1 bin]# hadoop fs -rm /shp.txt
```

#### 7、HDFS 客户端环境准备

1）、首先根据自己电脑操作系统拷贝对应的编译后的 hadoop 的 jar 包到非中文路径下（区分 win10 编译过的 hadoop 中 jar 包、win7编译过的 hadoop 中 jar 包、linux 编译过的 hadoop 中 jar 包）

2）、配置 HADOOP 环境变量

3）、创建项目，添加依赖

```xml
<dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-core</artifactId>
            <version>2.8.2</version>
        </dependency>
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-common</artifactId>
            <version>2.7.2</version>
        </dependency>
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-client</artifactId>
            <version>2.7.2</version>
        </dependency>
        <dependency>
            <groupId>org.apache.hadoop</groupId>
            <artifactId>hadoop-hdfs</artifactId>
            <version>2.7.2</version>
        </dependency>
    </dependencies>
```

#### 8、java 代码访问 hdfs

```java
public class HDFSClient {
    public static void main(String[] args) throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        //1.获取 hdfs 客户端对象
        /**
         * 第一个参数：hdfs 中 namenode 的地址
         * 第二个参数：配置类
         * 第三个参数：用什么用户去访问 hdfs
         */
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        //2.在 hdfs 上创建路径
        client.mkdirs(new Path("/shp/love"));

        //3.关闭资源
        client.close();
        System.out.println("访问结束");
    }
}
```

### HDFS 的 API 操作

#### 1、文件上传

```java
@Test
    public void testCopyFromLocalFile() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2.执行上传 API
        // 第一个参数是本地文件路径，第二个参数是 hdfs 上文件路径
        client.copyFromLocalFile(new Path("/Users/shenheping/Desktop/hello.txt"),new Path("/shp"));

        //3.关闭资源
        client.close();
    }
```

**参数优先级：**

① 我们将 `hdfs-site.xml` 拷贝到项目的类路径下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>

<configuration>
	<property>
		<name>dfs.replication</name>
        <value>1</value>
	</property>
</configuration>
```

这样你项目在运行的时候它会自动加载类路径下的配置文件，然后你在上传一个文件到 hdfs 上，发现副本数就变成了 1

② 直接在代码中设置副本数

```java
@Test
    public void testCopyFromLocalFile() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        configuration.set("dfs.replication","2");
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2.执行上传 API
        client.copyFromLocalFile(new Path("/Users/shenheping/Desktop/hello.txt"),new Path("/shp"));

        //3.关闭资源
        client.close();
    }
```

这样你再上传一个文件到 hdfs 上，发现副本数变成了 2

**参数优先级排序**

> 客户端代码中设置的值 > 类路径下用户自定义的配置文件 > 服务中配置文件配置的值

#### 2、文件下载

```java
@Test
    public void testCopyToLocalFile() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2. 执行下载 API
        client.copyToLocalFile(new Path("/heping.txt"),new Path("/Users/shenheping/Desktop"));

        // 3.关闭资源
        client.close();
    }
```

#### 3、文件夹删除

```java
@Test
    public void testDelete() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2. 执行删除 API
        // 第二个参数表示是否是递归删除
        client.delete(new Path("/heping.txt"),true);

        // 3.关闭资源
        client.close();
    }
```

#### 4、修改文件名称

```java
@Test
    public void testRename() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2.执行修改名称 API
        client.rename(new Path("/shp"),new Path("/shp1"));

        // 3.关闭资源
        client.close();
    }
```

#### 5、查看文件详情

查看文件名称、权限、长度、块信息

```java
@Test
    public void testListFiles() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2.查看文件详情
        RemoteIterator<LocatedFileStatus> listFiles = client.listFiles(new Path("/"), true);

        while (listFiles.hasNext()) {
            // 拿到这个文件的状态信息
            LocatedFileStatus fileStatus = listFiles.next();
            // 查看文件名称、权限、长度、块信息
            System.out.println(fileStatus.getPath().getName()); // 文件名称
            System.out.println(fileStatus.getPermission());  // 文件权限
            System.out.println(fileStatus.getLen());   // 文件长度

            // 返回一个数组，因为这个数据块会有多个副本
            BlockLocation[] blockLocations = fileStatus.getBlockLocations();
            for (BlockLocation blockLocation : blockLocations) {
                // 这个数据块具体在哪一台主机上
                String[] hosts = blockLocation.getHosts();
                for (String host : hosts) {
                    System.out.println(host);
                }
            }
            System.out.println("------分隔线-----");

        }
        // 3.关闭资源
        client.close();
    }
```

#### 6、判断是文件还是文件夹

```java
@Test
    public void testListStatus() throws URISyntaxException, IOException, InterruptedException {
        Configuration configuration = new Configuration();
        // 1.获取 hdfs 对象
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration, "root");

        // 2.判断操作
        FileStatus[] fileStatuses = client.listStatus(new Path("/"));
        for (FileStatus fileStatus : fileStatuses) {
            if (fileStatus.isFile()) {
                System.out.println("文件" + fileStatus.getPath().getName());
            } else if (fileStatus.isDirectory()) {
                System.out.println("目录" + fileStatus.getPath().getName());
            }
        }
    }
```

### HDFS 的 I/O 操作

前面我们都是使用 hdfs 封装好的 API 对 HDFS 进行操作，下面我们使用  IO 流对 HDFS 进行操作

#### 1、HDFS 文件上传

```java
/**
     * 把本地的文件上传到 hdfs 的根目录
     */
    @Test
    public void test() throws URISyntaxException, IOException, InterruptedException {
        // 1. 获取 hdfs 对象
        Configuration configuration = new Configuration();
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration,"root");

        // 2.获取输入流
        FileInputStream fis = new FileInputStream(new File("/Users/shenheping/Desktop/abc.txt"));

        // 3.获取输出流
        FSDataOutputStream fos = client.create(new Path("/abc.txt"));

        // 4.流的拷贝
        IOUtils.copyBytes(fis,fos,configuration);

        // 5.关闭流
        IOUtils.closeStream(fos);
        IOUtils.closeStream(fis);
        client.close();
    }
```

#### 2、HDFS 文件下载

```java
/**
     * 从 hdfs 上下载文件到本地
     */
    @Test
    public void getFileFromHDFS() throws URISyntaxException, IOException, InterruptedException {
        // 1. 获取 hdfs 对象
        Configuration configuration = new Configuration();
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration,"root");

        // 2.获取输入流
        FSDataInputStream fis = client.open(new Path("/abc.txt"));

        // 3.获取输出流
        FileOutputStream fos = new FileOutputStream(new File("/Users/shenheping/Desktop"));

        // 4.IO流对拷
        IOUtils.copyBytes(fis,fos,configuration);

        // 5.关闭资源
        IOUtils.closeStream(fos);
        IOUtils.closeStream(fis);
        client.close();
    }
```

#### 3、定位读取文件

分块读取 HDFS 上的大文件

```java
/**
     * 下载第一块
     */
    @Test
    public void readFileSeek1() throws URISyntaxException, IOException, InterruptedException {
        // 1.获取 fdfs 对象
        Configuration configuration = new Configuration();
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration,"root");

        // 2. 获取输入流
        FSDataInputStream fis = client.open(new Path("/hadoop-2.7.2.tar.gz"));

        // 3.获取输出流
        FileOutputStream fos = new FileOutputStream(new File("/Users/shenheping/Desktop/hadoop-2.7.2.tar.gz.part1"));

        // 4.流的拷贝（只拷贝 128m）
        byte[] bytes = new byte[1024];
        for (int i = 0; i < 1024 * 128; i++) {
            fis.read(bytes);
            fos.write(bytes);
        }

        // 5.关闭流
        IOUtils.closeStream(fos);
        IOUtils.closeStream(fis);
        client.close();
    }

    @Test
    public void readFileSeek2() throws URISyntaxException, IOException, InterruptedException {
        // 1.获取 fdfs 对象
        Configuration configuration = new Configuration();
        FileSystem client = FileSystem.get(new URI("hdfs://192.168.148.141:9000"), configuration,"root");

        // 2. 获取输入流
        FSDataInputStream fis = client.open(new Path("/hadoop-2.7.2.tar.gz"));

        // 3.设置指定读取的起点
        fis.seek(1024 * 1024 * 128);

        // 4.获取输出流
        FileOutputStream fos = new FileOutputStream(new File("/Users/shenheping/Desktop/hadoop-2.7.2.tar.gz.part1"));

        // 5.流的拷贝
        IOUtils.copyBytes(fis,fos,configuration);

        // 6.关闭流
        IOUtils.closeStream(fos);
        IOUtils.closeStream(fis);
        client.close();
    }
```







































































































































































