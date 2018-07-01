---
layout: post
title: Use Spark Submit for the first time
date: 2018-07-01 23:32:20 +0530
description: Using Spark Submit for the first time tutorial
img: spark-master.png 
tags: [Hackathon]
author: Rajiv Jha
---
July 1, 2018

Hello!

This article explains how to set-up spark submit to use applications via spark.

This article assumes that you have successfully downloaded and set-up the apache spark. If not, then please refer to http://rjrajivjha.tech/Setup-Spark-Standalone-Master-and-Slave/ 

Also, before moving ahead, please comment these environment variable from bash_profile, as they might cause error while submitting a standalone spark application.

`#export PYSPARK_DRIVER_PYTHON=jupyter`
`#export PYSPARK_DRIVER_PYTHON_OPTS='notebook'`

After commenting these path variables, you can go ahead and try the tutorial.

## Write your wordcount.py file

`"""Calculates the word count of the given file.`
`the file can be local or if you setup cluster.`
`It can be hdfs file path"""`
`## Imports`
`from pyspark import SparkConf, SparkContext`
`from operator import add`
`import sys`
`## Constants`
`APP_NAME = " HelloWorld of Big Data"`
`##OTHER FUNCTIONS/CLASSES`
`def main(sc,filename):`
   `textRDD = sc.textFile(filename)`
   `words = textRDD.flatMap(lambda x: x.split(',')).map(lambda x: (x, 1))`
   `wordcount = words.reduceByKey(add).collect()`
   `for wc in wordcount:`
      `print wc[0],wc[1]`
`if __name__ == "__main__":`
   `# Configure Spark`
   `conf = SparkConf().setAppName(APP_NAME)`
   `conf = conf.setMaster("local[*]")`
   `sc   = SparkContext(conf=conf)`
   `filename = sys.argv[1]`
   `# Execute Main functionality`
  `main(sc, filename)`
   
   
## Submit the Application to spark

> Navigate to spark directory where you have decompressed the downloaded tgz file.

`Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ Rajivs-Air:spark-2.3.1-bin-hadoop2.7 rjrajivjha$ bin/spark-submit --master spark://Rajivs-Air:7077 ~/Desktop/DataScienceChallenges/Sapient/wordcount.py  ~/Desktop/DataScienceChallenges/Sapient/household.csv `

I am using Spark URL, spark://Rajivs-Air:7077 , which can be found when you run standalone master and slave on spark.
Also, the absolute path to my wordcount.py program and absolute path to my targetted csv file.

Hope this helps!
Keep tuned for more blogs from my Spark and ML series.

Happy Learning!

Rajiv Jha :) 
