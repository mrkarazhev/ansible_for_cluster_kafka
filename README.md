 # **General**

This ansible configuration allows you to deploy a kafka cluster and a zookeeper on three nodes.

Three roles are created: \
The first installs docker (may need kafka-ui or different exporters for monitoring later) \
The second installs kafka and zookeeper \
The third one is wiring the configuration files.

Used this on an ***ubuntu 20.04 focal operating system*** \
**Kafka version 3.4.0 is used**


## **Options**

The ***all.yml*** file is the master playbook which specifies which roles are used. \
It also specifies variables, you will need to substitute in them the actual data for you, such as ip address, id broker ... but this is not the only file where variables are used.

The ***inventory file*** specifies the nodes on which the cluster will be deployed. It is divided into 3 groups - broker-1, broker-2, broker-3. In each of them you have to specify ip addresses of your servers and access details.


### Role of kafka-setup

The kafka-setup role consists of 4 directories :

***files*** - it stores files kafka.service and zookeeper.service (systemd services), server.properties.j2 - kafka configuration file , zookeeper.properties.j2 - zookeeper configuration file, there is also a hosts.j2 file so brokers can resolve each other
 
***handlers*** - it stores the configuration to restart services when configuration files are changed

***tasks*** - specifies the cluster configuration steps 

***vars*** - contains main.yml file, it uses variables for hosts file and zookeeper configuration file





