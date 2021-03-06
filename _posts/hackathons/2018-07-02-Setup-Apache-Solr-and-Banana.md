---
layout: post
title: Setup Apache Solr and Banana
date: 2018-07-02 23:32:20 +0530
description: Setup Apache Solr
img: solr.png 
tags: [Hackathon]
author: Rajiv Jha
---
July 2, 2018

Hello!

This article explains how to set-up Apache Solr and Banana.

This article assumes that you have successfully downloaded and set-up the apache solr. If not, then please download from https://www.apache.org/dyn/closer.lua/lucene/solr/7.3.1/solr-7.3.1-src.tgz


## Move to Root Directory of Apache Solr

Root directory is the directory where you have decompressed the tgz file, you downloaded from Apache Solr website.

`Rajivs-Air:~ rjrajivjha$ cd /usr/local/Cellar/solr/7.3.1/`


## Let's follow with lead

`Rajivs-Air:7.3.1 rjrajivjha$ ls`

`CHANGES.txt			example
INSTALL_RECEIPT.json		homebrew.mxcl.solr.plist
LICENSE.txt			libexec
NOTICE.txt			server
README.txt			share
bin`

## Start Solr

`Rajivs-Air:7.3.1 rjrajivjha$ bin/solr start`

*** [WARN] *** Your open file limit is currently 256.  
 
 It should be set to 65000 to avoid operational disruption. 
 
 If you no longer wish to see this warning, set SOLR_ULIMIT_CHECKS to false in your profile or solr.in.sh

*** [WARN] ***  Your Max Processes Limit is currently 709. 

It should be set to 65000 to avoid operational disruption. 

If you no longer wish to see this warning, set SOLR_ULIMIT_CHECKS to false in your profile or solr.in.sh

Waiting up to 180 seconds to see Solr running on port 8983 [/]  

Started Solr server on port 8983 (pid=19131). Happy searching!


## Create Core 

`Rajivs-Air:7.3.1 rjrajivjha$ bin/solr create -c ezpg`

WARNING: Using _default configset with data driven schema functionality. NOT RECOMMENDED for production use.
         To turn off: bin/solr config -c ezpg -p 8983 -property update.autoCreateFields -value false

Created new core 'ezpg'

## Copy Your Data to visualize

`Rajivs-Air:7.3.1 rjrajivjha$ cd example/exampledocs/`

`Rajivs-Air:exampledocs rjrajivjha$ cp ~/Desktop/Hackathon/ezpg/dataset/RawDataDuplicateRemoved.csv  .`

`Rajivs-Air:exampledocs rjrajivjha$ cp ~/Desktop/Hackathon/ezpg/dataset/RawDataExplored.csv  .`

`Rajivs-Air:exampledocs rjrajivjha$ ls`

RawDataDuplicateRemoved.csv	monitor2.xml

RawDataExplored.csv		more_books.jsonl

books.csv			mp500.xml

books.json			post.jar

gb18030-example.xml		sample.html

hd.xml				sd500.xml

ipod_other.xml			solr-word.pdf

ipod_video.xml			solr.xml

manufacturers.xml		test_utf8.sh

mem.xml				utf8-example.xml

money.xml			vidcard.xml

monitor.xml

## Post file to Solr

`Rajivs-Air:exampledocs rjrajivjha$ java -Dtype=text/csv -Dc=ezpg -jar post.jar  RawDataExplored.csv`

`SimplePostTool version 5.0.0
Posting files to [base] url http://localhost:8983/solr/ezpg/update using content-type text/csv...
POSTing file RawDataExplored.csv to [base]
1 files indexed.
COMMITting Solr index changes to http://localhost:8983/solr/ezpg/update...
Time spent: 0:01:00.474`

## Download banana and untar it

Link to download - https://github.com/lucidworks/banana 

## Copy Banana to Server and Run Server

`Rajivs-Air:7.3.1 rjrajivjha$ cd server/`

`Rajivs-Air:server rjrajivjha$ cd solr-webapp/`

`Rajivs-Air:solr-webapp rjrajivjha$ cd webapp/`

`Rajivs-Air:webapp rjrajivjha$ cp -r ~/Downloads/banana .`

> Link to Solar Dashboard - http://localhost:8983/solr/#/

> Link to Banana Dashboard - http://localhost:8983/solr/banana/src/index.html#/dashboard 

> Navigate to Core ezpg, which I created in browser

> Click on 'query' and then 'execute query' to view the data of your csv file

> To learn more about banana Dashboard, Keep tuned.

Hope this helps!
Keep tuned for more blogs from ML series.

Happy Learning!

Rajiv Jha :)
