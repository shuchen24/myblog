# 手把手教你搭建spark & hdfs

本篇文章旨于从头搭建__spark & hdfs(hadoop distributed file system)__ in standalone生产环境，适合于小白。ps my os is arch linux ,dont worry, it's still suit for linux user
## introduce
__spark standalone__:除了在Mesos或者YARN上运行集群管理器,spark还提供了简单的独立部署模式。可以通过手动启动,或者使用spark提供的启动脚本,启动一个独立的集群。它可以运行在一台机器上

__hdfs__:HDFS是一个分布式文件系统，可提供跨Hadoop集群数据的高性能访问,已成为管理大数据池和支持大数据分析应用的关键工具。

在读完本篇教程后，你将可以通过spark来获取HDFS中问的文件并进行简单的数据处理。

## install spark
### step 1 verify java installation
运行命令
```
java -version
```
if installed,then show like this
```
java version "1.7.0_95"
OpenJDK Runtime Environment (IcedTea 2.6.4) (Arch Linux build 7.u95_2.6.4-1-x86_64)
OpenJDK 64-Bit Server VM (build 24.95-b01, mixed mode)
```
if not ,use this link
```
https://java.com/en/download/help/linux_x64_install.xml
```
### step 2 install scala

http://www.scala-lang.org/download/
通过这个链接下载scala tgz包，运行
```
cd <the path you Download scala>
tar xvf scala-2.11.7.tgz
sudo mv scala-2.11.7 /usr/local/scala
```
为scala设置环境变量
在本例中，添加下面的句子到.bashrc中
export PATH = $PATH:/usr/local/scala/bin
```
vim ~/.bashrc
source ~/.bashrc
```
然后，运行
```
scala -version
```
若成功，你将看到
```
Scala code runner version 2.11.7 -- Copyright 2002-2013, LAMP/EPFL
```
### step 3 install spark
在这里，笔者下载的是spark 1.6.0的预编译版，支持Hadoop 2.4及之后的版本.
```
wget http://apache.fayea.com/spark/spark-1.6.0/spark-1.6.0bin-hadoop2.4.tgz
cd <the path you Download spark>
tar xvf spark-1.6.0-bin-hadoop2.6.4.tgz
sudo mv spark-1.6.0-bin-hadoop2.6.4 /usr/local/spark
```
为spark设置环境变量
在本例中，添加下面的句子到.bashrc中
export PATH = $PATH:/usr/local/spark/bin
```
vim ~/.bashrc
source ~/.bashrc
```
然后，运行
```
spark-shell
```
若成功，你将看到
```
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /___/ .__/\_,_/_/ /_/\_\   version 1.6.0
      /_/
```
## install Hadoop
