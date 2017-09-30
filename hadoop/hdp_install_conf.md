#总体步骤
- 集群中所有机器配置相同的host文件
- 集群中机器配置相互登录免密码
- 安装JDK并设置JAVA_HOME环境变量
- 安装hadoop，并设置core-site.xml hdfs-site.xml yarn-site.xml 
- mapred-site.xml master slave hadoop-env.sh
- 格式化HDFS
- 启动hadoop集群
- 验证hadoop集群

# 1 准备工作：
- 因为hadoop分布式集群在工作中master与slave间需登录执行操作，故相互间
- 需要设置免密码登录
# 2 配置相同的host文件
# 3 软件包：JDK  Hadoop
## 3.1 jdk安装后配置JAVA_HOME环境变量
> vim /etc/profile
> source /etc/profile
## 3.2 安装hadoop：解压hadoop-x.x.x-tar.gz
# 4 配置hadoop

 vim core-site.xml
> <property>
>    <name>fs.default.name</name>
>    <value>hdfs://bigdata:9000</value>
>  </property>
>
> <property>
>    <name>hadoop.tmp.dir</name>
>    <value>/opt/hadoop-2.7.2/current/tmp</value>
>  </property>
> <property>
>    <name>fs.trash.interval</name>
>    <value>4320</value>
>  </property>

vim hdfs-site.xml
><property>
>   <name>dfs.namenode.name.dir</name>
>   <value>/opt/hadoop-2.7.2/current/dfs/name</value>
> </property>
> <property>
>   <name>dfs.datanode.data.dir</name>
>   <value>/opt/hadoop-2.7.2/current/data</value>
> </property>
> <property>
>   <name>dfs.replication</name>
>   <value>1</value>
> </property>
> <property>
>   <name>dfs.webhdfs.enabled</name>
>   <value>true</value>
> </property>
> <property>
>   <name>dfs.permissions.superusergroup</name>
>   <value>staff</value>
> </property>
> <property>
>   <name>dfs.permissions.enabled</name>
>   <value>false</value>
> </property>

vim yarn-site.xml
><property>
>   <name>yarn.resourcemanager.hostname</name>
>   <value>bigdata</value>
> </property>
> <property>
>   <name>yarn.nodemanager.aux-services</name>
>   <value>mapreduce_shuffle</value>
> </property>
> <property>
>   <name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
>   <value>org.apache.hadoop.mapred.ShuffleHandler</value>
> </property>
> <property>
>   <name>yarn.resourcemanager.address</name>
>   <value>bigdata:18040</value>
> </property>
><property>
>   <name>yarn.resourcemanager.scheduler.address</name>
>   <value>bigdata:18030</value>
> </property>
> <property>
>   <name>yarn.resourcemanager.resource-tracker.address</name>
>   <value>bigdata:18025</value>
> </property> <property>
>   <name>yarn.resourcemanager.admin.address</name>
>   <value>bigdata:18141</value>
> </property>
><property>
>   <name>yarn.resourcemanager.webapp.address</name>
>   <value>bigdata:18088</value>
> </property>
><property>
>   <name>yarn.log-aggregation-enable</name>
>   <value>true</value>
> </property>
><property>
>   <name>yarn.log-aggregation.retain-seconds</name>
>   <value>86400</value>
> </property>
><property>
>   <name>yarn.log-aggregation.retain-check-interval-seconds</name>
>   <value>86400</value>
> </property>
><property>
>   <name>yarn.nodemanager.remote-app-log-dir</name>
>   <value>/tmp/logs</value>
> </property>
><property>
>   <name>yarn.nodemanager.remote-app-log-dir-suffix</name>
>   <value>logs</value>
> </property>

vim mapred-site.xml

><property>
>  <name>mapreduce.framework.name</name>
>  <value>yarn</value>
></property>
><property>
>  <name>mapreduce.jobtracker.http.address</name>
>  <value>bigdata:50030</value>
></property>
><property>
>  <name>mapreduce.jobhisotry.address</name>
>  <value>bigdata:10020</value>
></property>
><property>
>  <name>mapreduce.jobhistory.webapp.address</name>
>  <value>bigdata:19888</value>
></property>
><property>
>  <name>mapreduce.jobhistory.done-dir</name>
>  <value>/jobhistory/done</value>
></property>
><property>
>  <name>mapreduce.intermediate-done-dir</name>
>  <value>/jobhisotry/done_intermediate</value>
></property>
><property>
>  <name>mapreduce.job.ubertask.enable</name>
>  <value>true</value>
></property>

vim master

> master

vim slave
> slave1
> slave2

vim hadoop-env.sh
> JAVA_HOME

# 5 格式化HDFS

> hdfs namenode -format

# 6 启动hadoop集群

> /opt/hadoop-2.7.2/sbin/start-all.sh

# 7 验证hadoop集群

1 jps
2
- hdfs http://bigdata:50070
- yarn http://bigdata:18088

