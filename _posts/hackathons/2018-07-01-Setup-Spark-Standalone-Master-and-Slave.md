---
layout: post
title: Setup Spark Standalone Master and Slave
date: 2018-07-01 23:32:20 +0530
description: Setup Spark Standalone Master and Slave on MacOs
img: spark-master.png 
tags: [Hackathon]
author: Rajiv Jha
---
July 1, 2018

Hello!

This article explains how to set-up spark standalone master and slave from command-line.

Download Apache Spark binaries from Mirror site. Official Documentation and downloads available at https://spark.apache.org/downloads.html

I have downloaded Spark and decompressed the file in Downloads folder. Now open the command prompt / terminal and let's dive deep.


## Set up the Environment Variable by opening Your bash_profile or bashrc (wherever you have saved your environment variables)

Update the .bash_profile with these lines, and save with command+x and source the bash_profile.

nano .bash_profile

//edit the paths

save and exit with command+x

source .bash_profile 

` export SPARK_HOME=~/Downloads/spark-2.3.1-bin-hadoop2.7

export PATH=$SPARK_HOME/bin:$PATH

export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_161.jdk/Contents/Ho$

export PATH=$JAVA_HOME:$PATH

export PYSPARK_DRIVER_PYTHON=jupyter

export PYSPARK_DRIVER_PYTHON_OPTS='notebook' `

## Start Master 

> Navigate to spark directory where you have decompressed the downloaded tgz file.

`Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ ./sbin/start-master.sh `

You can now look at localhost:8080 to check the spark-master.
There you will find the Spark URL as well. Use the same spark url to start the slave.

## Start Slave with Spark Url

`Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ ./sbin/start-slave.sh spark://Rajivs-Air:7077 

Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ ./sbin/start-slave.sh spark://Rajivs-Air:7077 --cores 2 --memory 4g `


## Stop Slave

`Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ ./sbin/stop-slave.sh`

## Stop Master and all other processes 

`Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ ./sbin/stop-all.sh `



Keep tuned for more blogs from my Spark and ML series.

Happy Learning!

Rajiv Jha :) 
