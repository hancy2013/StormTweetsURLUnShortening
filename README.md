# StormTweetsURLShortening

## Introduction
Forked and updated from [Michael Vogiatzis's storm-unshortening] (https://github.com/mvogiatzis/storm-unshortening).<br>
This repository contains an application which is built to demonstrate an example of Storm distributed framework.

You can find Storm [here] (http://storm-project.net).
This application is compatible and developed with Storm v0.8.2. This application has been tested with Storm v0.8.2. Application might or might not work with earlier or later versions than Storm v0.8.2.

This application reads tweets from Twitter stream (using Twitter4J) and in real-time unshortens the urls found in the tweets using 3rd party calls from [Unshort.me] (http://unshort.me).<br>
It logs the short-resolved url pairs to the console and also to a log file.<br>
It can also write the short-resolved url pairs into a urlshorten.cassandra table; currenly this functionality is commented out.<br>

Check the [config.properties](src/main/resources/config.properties) and insert your own values and complete the integration of Twitter API to your application by looking at your values from [Twitter Developer Page] (https://dev.twitter.com/apps). If you did n't create an app before, create a new Twitter App which will create all these values afresh and then populate them here withour any mistake.<br>
## Requirements
This project uses Maven to build and run.
* Sun / Oracle JDK >= 1.7.x
* Apache Maven >= 3.0.5
* Requires ZooKeeper, JZMQ, ZeroMQ installed and configured in case of executing this project in distributed mode i.e. Storm Cluster.<br>
	- Follow the steps mentioned [here] (https://github.com/nathanmarz/storm/wiki/Setting-up-a-Storm-cluster) for more details on setting up a Storm Cluster.<br>

Rest of the required frameworks and libraries are downloaded and configured using Maven.
## Usage
### Local Mode:
Local mode can also be run on Windows environment without installing any specific software or framework as such.<br>
In local mode, this application can be run from command line.<br>

    mvn clean compile exec:java -Dexec.classpathScope=compile -Dexec.mainClass=urlshorten.topology.UnshortenTopology

or

    mvn clean compile package && java -jar target\StormTweetsURLShortening-1.0.0-SNAPSHOT-jar-with-dependencies.jar
	
### Distributed [or Cluster / Production] Mode:
Distributed mode requires a complete and proper Storm Cluster setup.<br>
In distributed mode, after starting Nimbus and Supervisors on individual machines, this application can be executed on the master machine by invoking the following on the command line:

    storm jar target\StormTweetsURLShortening-1.0.0-SNAPSHOT-jar-with-dependencies.jar urlshorten.topology.UnshortenTopology UnshortenURLs

## Feedback
If you find any issues, please do ping me either raising an issue here on Github or on my Twitter handle [@P7h] (http://twitter.com/P7h).
Appreciate your help. Thanks.