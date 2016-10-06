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

 
####Using the Twitter Streaming API 
In order to download the tweets from twitter streaming API and push them to kafka queue, I have created a python script
app.py. The script will need your twitter authentication tokens (keys).

Once you have your authentication tokens, create or update the `twitter-app-credentials.txt` with these  credentials.

After updating the text file with your twitter keys, you can start downloading tweets from the twitter stream API and push them to the twitterstream topic in Kafka. Do this by running the script as follows:   
`$ python app.py`   
Note: This program should be kept running for collecting tweets. 
 
#####To check if the data is landing in Kafka: 
`$ bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic twitterstream --from-beginning`

#####Running the Stream Analysis Program:
`$ $SPARK_HOME/bin/spark-submit --packages org.apache.spark:spark-streaming-kafka_2.10:1.5.1 twitterStream.py`
