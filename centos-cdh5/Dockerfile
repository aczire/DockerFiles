# CDH5 
FROM aczire/centos7-ssh
MAINTAINER Jimson K James "mail.jimson@aczire.com"
ENV REFRESHED_AT 2014-12-01

# Install CDH5 core and GPL Extras Repositories
RUN rpm -Uvh http://archive.cloudera.com/cdh5/one-click-install/redhat/6/x86_64/cloudera-cdh-5-0.x86_64.rpm
RUN rpm --import http://archive.cloudera.com/cdh5/redhat/6/x86_64/cdh/RPM-GPG-KEY-cloudera
RUN curl http://archive.cloudera.com/gplextras5/redhat/6/x86_64/gplextras/cloudera-gplextras5.repo \
 -o /etc/yum.repos.d/cloudera-gplextras5.repo

#RUN yum update

# Hadoop core packages
RUN yum install -y hadoop-yarn-resourcemanager hadoop-hdfs-namenode hadoop-hdfs-secondarynamenode \
    hadoop-yarn-nodemanager hadoop-hdfs-datanode hadoop-mapreduce \    
    hadoop-mapreduce-historyserver hadoop-yarn-proxyserver hadoop-client

# Install Hadoop pseudo distributed mode configurations
RUN yum install -y hadoop-conf-pseudo

# Install LZO from GPL Extras
RUN	yum install -y hadoop-lzo

# Hadoop ecosystem packages
#
# Zookeeper
RUN yum install -y zookeeper zookeeper-server

RUN mkdir -p /var/lib/zookeeper
RUN chown -R zookeeper /var/lib/zookeeper/

RUN service zookeeper-server init
RUN service zookeeper-server start
 
# HBase
RUN yum install -y hbase

# Hive
RUN yum install -y hive

# Oozie
RUN yum install -y oozie oozie-client

# Pig
RUN yum install -y pig pig-udf-datafu

# Spark
RUN yum install -y spark-core spark-master spark-worker spark-history-server spark-python

# Hue
RUN yum install -y hue hue-plugins

# Format namenode
RUN hdfs namenode -format
