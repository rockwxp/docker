Check the current directory (optional)
Do a ls -l on the current directory it should have the two files we created above

docker-3 % ls -l
-rw-r--r-- 1 hadoop apache 2547 Jun 23 15:53 config
-rw-r--r-- 1 hadoop apache 1533 Jun 23 16:07 docker-compose.yaml
Run the docker containers
Run the docker containers using docker-compose

docker-compose up -d
The output should look like:

docker-3 % docker-compose up -d  
Creating network "docker-3_default" with the default driver
Creating docker-3_namenode_1 ... done
Creating docker-3_datanode_1 ... done
Creating docker-3_nodemanager_1 ... done
Creating docker-3_resourcemanager_1 ... done
Accessing the Cluster:
Login into a node:

Can login into any node by specifying the container like:

docker exec -it docker-3_namenode_1 /bin/bash
Running an example Job (Pi Job)

yarn jar share/hadoop/mapreduce/hadoop-mapreduce-examples-3.3.5.jar pi 10 15
The above will run a Pi Job and similarly any hadoop related command can be run.

Accessing the UI
The Namenode UI can be accessed at http://localhost:9870/⁠ and the ResourceManager UI can be accessed at http://localhost:8088/⁠

Shutdown Cluster
The cluster can be shut down via:

docker-compose down
