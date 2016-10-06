#Twitter Sentiment Analytics using Apache Spark Streaming APIs and Python 

In this project, I learnt about processing live data streams using Spark’s streaming APIs and Python. I performed a basic sentiment analysis of real-time tweets. In addition, I also got a basic introduction to Apache Kafka, which is a queuing service for data streams. 

##Requirements
One of the first requirements is to get access to the streaming data; in this case, real-time tweets. Twitter provides a very 
convenient API to fetch tweets in a streaming manner 
 
In addition, I also used Kafka to buffer the tweets before processing. Kafka provides a distributed queuing service which can be used to store the data when the data creation rate is more than processing rate. It also has several other uses. 

###Project Setup 
 
####Installing Required Python Libraries 
I have provided a text file containing the required python packages: `requirements.txt`

To install all of these at once, simply run (only missing packages will be installed):    
`$ sudo pip install -r requirements.txt`
 
####Installing and Initializing Kafka 
Download and extract the latest binary from https://kafka.apache.org/downloads.html

#####Start zookeeper service:  
`$ bin/zookeeper-server-start.sh config/zookeeper.properties`
 
#####Start kafka service: 
`$ bin/kafka-server-start.sh config/server.properties`
 
#####Create a topic named twitterstream in kafka: 
`$ bin/kafka-topics.sh --create --zookeeper --partitions 1 --topic twitterstream localhost:2181 --replication-factor 1`
