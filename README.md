# HOW TO MAKE DOCKERFILE FOR ELASTICSEARCH | HOW TO INSTALL AND CONFIGURE ELASTICSEARCH WITH THE DOCKER
Elasticsearch is a popular open-source search and analytics engine for use cases such as log analytics, real-time application monitoring, and click stream analytics.

For the above things we have to follow these steps and assume that you have Linux OS in your system and Docker engine are running.

Make a Docker file with Ubuntu 16.04 Base image
Build Image from Dockerfile

Run Docker Container

To configure your elasticsearch server execute the container and configure as per your requirements
DOCKERFILE TO BUILD ELASTICSEACRH IMAGE

# BUILD IMAGE FROM DOCKERFILE

Example: # docker  build  –t  <tag= repo/imagename>
 docker   build –t  rahulkathpal/elasticsearch   .

docker    images

REPOSITORY                 TAG     IMAGE ID       CREATED       SIZE

rahulkathpal/elasticseacrh  latest  3739ab6g6f4e   10sec ago     1.54GB

RUN DOCKER CONTAINER

Example: # docker run –it    -p   --name   -d     

 docker  run  –it  -p 9200:9200 --name elasticsearch-server   –d  3739ab6g6f4e   /bin/bash

Now we can see that our elasticsearch-server are running.

docker ps 

docker     exec  –it   elasticsearch-sever     bash

TO CONFIGURE YOUR ELASTICSEARCH SERVER EXECUTE THE CONTAINER AND CONFIGURE AS PER YOUR REQUIREMENT.

There are basic configuration shown as example


root@f8249c02deae:~# vim /etc/elasticsearch/elasticsearch.yml

Uncomment these lines if not available add these.


## Use a descriptive name for your cluster:
 cluster.name: linux-point-development
# -------------------- Node -----------------
## Use a descriptive name for the node:
 node.name: Tech-Blog
## -------------- Memory -------------------------
## Lock the memory on startup:
 bootstrap.memory_lock: true
## -------------- Network -------------------
## Set the bind address to a specific IP (IPv4 or IPv6):
##
 network.host: 127.0.0.1
 network.publish_host: localhost
 ##network.bind_host: 0.0.0.0
## network.bind_host: 0.0.0.0
## Set a custom port for HTTP:
 http.port: 9200-9300
##

root@f8249c02deae:~# service elasticsearch start


Test the elasticsearch server are running

root@f8249c02deae:~#  curl http://localhost:9200

{
  "name" : "Tech-Blog",
 "cluster_name" : "linux-point- development ",
  "cluster_uuid" : "huIY_z9fQnWhdUiQrqfyLA",
   "version" : {
     "number" : "2.4.5",
     "build_hash" : "19c13d0",
     "build_date" : "2017-07-18T20:44:24.823Z",
     "build_snapshot" : false,
     "lucene_version" : "6.6.0"
 },
  "tagline" : "You Know, for Search"
}

press ctrl+D to exit from container and test from base Machine

Now with your Public/Private IP you can See in browser by http://<ip>:9200

If you are using AWS EC2 intance as Base Server so you have to open Port 9200 for 0.0.0.0 and ::0 to anywhere in security group which is associated with your EC2 Instance.

Like and share @Thank you!

