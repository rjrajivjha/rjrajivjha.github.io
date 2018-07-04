---
layout: post
title: Kafka Tutorial - Part I
date: 2018-07-05 02:32:20 +0530
description: Basic Kafka Introduction
img: kafka-zookeeper.png
tags: [Hackathon]
author: Rajiv Jha
---
July 5, 2018

Hello!

I am starting with the Kafka Series. The article in this series are meant for aspiring data scientist (like Me), who wish to learn full stack Big Data & Machine Learning pipeline.

I will be referring to various sources of knowledge, and list them under Reference section of the article.

# Introduction

> Kafka is a distributed streaming platform. 
> It is used to simplify data pipelines that are made up of vast number of producers and consumers.
> Kafka gives you a stream and you can plugin a processing framework.
> There are no plug and play components. To customize, You need to learn the basics of kafka.

# Components

> Producers

 - Produces is an application that sends data to kafka
 - It is a small to medium size data
 - For kafka, it is simple array of bites.
 - If you want to send a file to kafka, Create a producer application and send each line of file as a message.
 - A message is one line of text.
 - If want to send a record, each row will be a message.
 - If you want to send the result of a query. create a producer application, run the query, fetch result and send each row as message.
 
> Connectors 

  - Database, they import data from database to kafka and export as well.

> Stream Processors

> Cluster 

  - It is a group of computer acting together for a common purpose.
  - Cluster, Each executing one instance of kafka brokers.

> Broker 

  - Is a Kafka server.
  - It is agent to exchange messages.
  
> Consumers

  - It recieves data.
  - Producer don't send data to receipeint address. producer send the message to kafka server.
  - Anyone who is interested in that data, can come forward and request the information, provided they have permission to read it.
  - If you want to read a file, create a consumer application and request kafka for the data.
  - Client application will recieve a lines of message.

> Topic 
  
  - Unique name for stream of data or Kafka Stream.

> Partitions

  - Data can be larger than storage capacity of single computer.
  - Obvious solution, is to distribute the data on different systems.
  - Break the data into partitions, and store.
  - When we create a topic, we give the argument for partition.
  - Every partition sits on a single system.
  
> Offset
  
  - This is a sequence number assigned to message arrived partition.
  - Immutable
  - It starts from 0.
  - There is no global offset across partition.
  - To locate a message, Topic , Partition and offset.

> Consumer Group

  - It is a group of consumers dividing the task among themselves.
  - eg. help in writing the data to data center
  
* Partition and consumer groups are tool for scalability.
* Maximum number of the consumers in a group, is total number of partitions on the topic.
* Kafka doesn't allow more than 2 consumer from the same partition, simultaneously.

> To learn more about Apache Kafka, Stay Tuned.

Hope this helps!
Keep tuned for more blogs from ML series.

Happy Learning!

Rajiv Jha :)
