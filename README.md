# Kafka-Installation
In this project, we will install kafa and Zookeeper. We will also try Kafka Producer and Consumer. 

## Check for Maven and OpenJDk
* Install Maven and OpenJDK and verify or (If you already have them then just do upgrade using ```choco upgrade all -y```
* Then hit these commands
 * ```refeshenv```
 * ```choco list -l```
 * ```java --version```
 * ```mvn -v```

## Install kakfa with Zoopkepper
* Go to "https://kafka.apache.org/quickstart" and click download and download the recommended version
* Un-tar it (using Bash) and change into the directory. Run this command ```tar -xzf <filename>``` ( In my case- tar -xzf kafka_2.13-2.6.0.tgz) 
* Check your Kafka Folder and check for these files/folders
  * ```bin```
  * ```bin/windows```
  * ```config (view some of the properties files)```
  * ```libs```
 
 ## Edit Environment Variables
 * Find Environment Variables in your device and open it
 * Go to System Variables and Check these variables; If not found make new one 
   * ```JAVA_HOME = C:\Program Files\OpenJDK\jdk-version folder```
   * ```KAFKA_HOME =  C:\kafka-version folder```
   * ```M2_HOME = C:\ProgramData\chocolatey\lib\maven\apache-maven-version```
 * Go to path, double click it and repeat the same process
   *  ```%JAVA_HOME%\bin OR C:\Program Files\OpenJDK\jdk-version\bin (or similar, NOT both!)```
   *  ```%M2_HOME%\bin```
   *  ```%KAFKA_HOME%\bin```
   *  ```%KAFKA_HOME%\bin\windows```
 
 ## Try Some Kafka Commands now
 ### Open different poweshell for different commands.
* ```.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties ``` this command will run Zookeeper service
* ``` .\bin\windows\kafka-server-start.bat .\config\server.properties ``` this command will start the kafka service
* ```.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic <topic>``` this command will create a kafka topic 
* For mine it was
   *  ```.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic lastweekend-result``` and 
   *  ```.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic football-fixtures```
 * ``` .\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --list ``` this command will list the created topics 
 * ```.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --delete --topic <topic> ``` this command will delete the topic you named 
* For mine it was 
 * ```.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --delete --topic lastweekend-result``` 
* Now let's  run Kafka Producer (will provide a > prompt for writing messages)
``` .\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic football-fixtures ``` this command will allow you to send the messages to the topic
* Now let's run Kafka Consumer (to show messages from the beginning)
``` .\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic football-fixtures --from-beginning``` this command will display the messages sent to the topic 


 
