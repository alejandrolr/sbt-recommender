# sbt-recommender

This recommender is deployed using the SBT tool. In addition, it will use hadoop to locate the dataset in the route hdfs://hadoop-master:9000.

Firstly it is needed to deploy the hadoop system, follow this tutorial: https://github.com/alejandrolr/hadoop-cluster

It will create the docker network `hadoop` for the communication between containers. Once deployed, you must execute these following commands:

```
sudo docker pull alejandrolr/recommender-hadoop:latest

docker run --net=hadoop -it alejandrolr/recommender-hadoop:latest
```
Once inside the container go to the path sbt-recommender:
```
cd /sbt-recommender
```

The code is in the folder ./src/main/scala, you can edit and recompile executing:
```
sbt compile 
```
Once compiled, you can package the program with:
```
sbt package
```

Once packaged, run the recommender executing:
```
spark-submit ./target/scala-XXX/recommender-XXX.jar
```
