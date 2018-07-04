---
layout: post
title: Kafka Tutorial - Part II
date: 2018-07-05 02:32:20 +0530
description: Kafka Tools
img: kafka-zookeeper.png
tags: [Hackathon]
author: Rajiv Jha
---
July 5, 2018

Hello!

This is 2nd part of the Kafka Series. The article in this series are meant for aspiring data scientist (like Me), who wish to learn full stack Big Data & Machine Learning pipeline.

I will be referring to various sources of knowledge, and list them under Reference section of the article.

# Basics of Kafka - Setup-First-Kafka-Message-Stream-From-Command-Line 

> Follow this tutorial - http://rjrajivjha.tech/Setup-First-Kafka-Message-Stream-From-Command-Line/ 

* Keep in Mind - If you don't create a topic and send a message from producer, kafka will create a topic on it's own.

# Fault Tolerance in Apache Kafka

> Enabling the availability of data, even in case of failure of system.
> Kafka keep "n" copies on "n" different system.
> Replication factor - Making multiple copies.
> Define replication factor at a topic, and it applies to all partition within a topic
> Kafka implements a leader and follower model.
> A broken is shortlisted as leader.
> Producer connects to leader and it's leader responsibility to do handshake with producer and consumer.
> For every partition, we have a leader.
> Kafka will identify n-1 broker as a follower and they copy data from leader.

# Steps to start New Brokers (Multi Node cluster on single machine)

> copy config/server.properties file and modify it as config/server-1.properties and config/server-2.properties .

> Modify
 - broker.id , change 0 to 1 for broker1, 2 for broker2.
 - listeners , increment the default value for broker1 and broker2.
 - log.dirs , change it as well with 1 for broker1 and 2 for broker 2. 

> Run Broker 1 -  bin/kafka-server-start.sh config/server.properries
> Run Broker 2 - bin/kafka-server-start.sh config/server-1.properries
> Run Broker 3 - bin/kafka-server-start.sh config/server-2.properries

Now you have 3 node kafka cluster up and running.

> Create the topic : bin/kafka-topics.sh --zookeeper localhost:2181 --create --topic TopicName --partitions 2 --replication-factor 3

> Describe the topic : bin/kafka-topics.sh --zookeeper localhost:2181 --describe --topic TopicName

* Everything listed is self explanatory but ISR, In sync replica - show the list of replica in sync with leader.

# Key Broker Configurations

- Zookeeper.connnect 
  - take zookeeper connection string, i.e host name and port number
  - every broker knows the zookeeper address
  - this is necessary for cluster forming
  - In cluster, all brokers know about each other, and zookeeper forms a link.
  
- delete.topic.enable 
  - By default, deleting a topic is not allowed.
  - Protection for production environment.

- auto.create.topics.enable
  - True for dev environment
  - might keep, False for production environment.
  
- default.replication.factor & num.partitions
  - default value : 1
  - effective when auto topic enable is 1
  
- log.retention.ms
  - Kafka don't retain the message, it give you option to retain it by time.
  - default period : 7 day
  
- log.retention.bytes
  - Another option to define the retention period, specify it by partition size.
  - kafka will trigger a cleanup activity, when the creteria meets. 
  
> To learn more about Apache Kafka, Stay Tuned.

Hope this helps!
Keep tuned for more blogs from ML series.

Happy Learning!

Rajiv Jha :)
