---
layout: post
title: Setup First Kafka Message Stream From Command Line 
date: 2018-04-18 23:32:20 +0530
description: Setup Kafka and ZooKeeper on MacOs
img: kafka-zookeeper.png 
tags: [Hackathon]
author: Rajiv Jha
---
June 30, 2018

Hello!

This article explains how to set-up apache Kafka and zookeeper and start your first streaming of messages from command-line.

Download Apache Kafka binaries from Mirror site. Official Documentation and downloads available at https://kafka.apache.org/downloads

I have downloaded Kafka and decompressed the file in Documents folder. Now open the command prompt / terminal and let's dive deep.


## Start Zookeeper server

`Rajivs-Air:Documents rjrajivjha$ cd kafka_2.12-1.1.0/`

`Rajivs-Air:kafka_2.12-1.1.0 rjrajivjha$ ./bin/zookeeper-server-start.sh config/zookeeper.properties`

## Start Kafka Server 


`Last login: Sat Jun 30 01:52:17 on ttys003`

`Rajivs-Air:~ rjrajivjha$ cd Documents/kafka_2.12-1.1.0`

`Rajivs-Air:kafka_2.12-1.1.0 rjrajivjha$ ./bin/kafka-server-start.sh config/server.properties`


## Create Topic 

`Rajivs-Air:~ rjrajivjha$ cd Documents/kafka_2.12-1.1.0`

`Rajivs-Air:kafka_2.12-1.1.0 rjrajivjha$ ./bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test`

`Created topic "test".`


## Run Producer

`Rajivs-Air:Documents rjrajivjha$ cd kafka_2.12-1.1.0`

`Rajivs-Air:kafka_2.12-1.1.0 rjrajivjha$ ./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test`

`>my first message`

`>my second message`

`>my third message`

`>wow`

`>Type your next message here to be produced at consumer end`


## Run Consumer 



`Last login: Sat Jun 30 02:06:16 on ttys005`

`Rajivs-Air:~ rjrajivjha$ cd Documents/kafka_2.12-1.1.0`

`Rajivs-Air:kafka_2.12-1.1.0 rjrajivjha$ ./bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning`

`my first message`

`my second message`

`my third message`

`wow`


Keep tuned for more blogs from my " Kafka-Zookeeper and Pyspark " series.

Happy Learning!

Rajiv Jha :) 
