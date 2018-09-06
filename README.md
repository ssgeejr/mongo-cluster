docker-compose (mongodb)
https://github.com/msound/localmongo/blob/4.0/docker-compose.yml
https://gist.github.com/garycrawford/0a45f820e146917d231d
https://github.com/yeasy/docker-compose-files
https://docs.mongodb.com/manual/tutorial/expand-replica-set/
https://docs.mongodb.com/manual/reference/configuration-options/

https://gist.github.com/mathieulaporte/d43fe9afe1b6a67f41c0
rs.initiate()
rs.conf() // to check conf
rs.status() // replica status


quetion: docker namespace ... 


On Linux, a default /etc/mongod.conf configuration file is included when using a package manager to install MongoDB.

### PACT Suite (library/local copy/ test case generating & testing 
# Jacococo
# Sonar
# Checkmarx
# PACTs Broker



docker exec -ti localmongo1 /bin/bash


https://towardsdatascience.com/how-to-deploy-a-mongodb-replica-set-using-docker-6d0b9ac00e49




https://stackoverflow.com/questions/43733112/how-to-create-mongodb-cluster-as-docker-containers



https://stackoverflow.com/questions/13912765/how-do-you-connect-to-a-replicaset-from-a-mongodb-shell
https://github.com/sclorg/mongodb-container/tree/master/examples/replset-docker

##  ---------------------------------------------------------------

https://groups.google.com/forum/#!topic/mongodb-user/3wFaE8RTV7U
usr/bin/mongod -f /etc/mongod.conf

# mongod.conf

# for documentation of all options, see:
#   http://docs.mongodb.org/manual/reference/configuration-options/

# Where and how to store data.
storage:
  dbPath: /var/lib/mongodb
  journal:
    enabled: true
#  engine:
#  mmapv1:
#  wiredTiger:

# where to write logging data.
systemLog:
  destination: file
  logAppend: true
  path: /var/log/mongodb/mongod.log

# network interfaces
net:
  port: 27017
  bindIp: 0.0.0.0


#processManagement:

security:
  keyFile: /opt/mongodb/keyfile

#operationProfiling:

replication:
  replSetName: app1r0


#sharding:

## Enterprise-Only Options:

#auditLog:

#snmp


##  ---------------------------------------------------------------

config = {
  	"_id" : "mongo_cluster",
  	"members" : [
  		{
  			"_id" : 0,
  			"host" : "mongo1:27017"
  		},
  		{
  			"_id" : 1,
  			"host" : "mongo2:27017"
  		},
  		{
  			"_id" : 2,
  			"host" : "mongo3:27017"
  		}
  	]
  }
  
  
> use admin
switched to db admin
> db.runCommand("getCmdLineOpts")
{
    "argv" : [
        "mongod",
        "--dbpath",
        "/data/db",
        "--replSet",
        "rs0"
    ],
    "parsed" : {
        "replication" : {
            "replSet" : "rs0"
        },
        "storage" : {
            "dbPath" : "/data/db"
        }
    },
    "ok" : 1
}
  
  
docker network create my-mongo-cluster
  
  
docker run \
-ti \
-p 30001:27017 \
--name mongo1 \
--net my-mongo-cluster \
mongo mongod --replSet my-mongo-set
  
docker run \
-ti \
-p 30002:27017 \
--name mongo2 \
--net my-mongo-cluster \
mongo mongod --replSet my-mongo-set 
  
docker run \
-ti \c
-p 30003:27017 \
--name mongo3 \
--net my-mongo-cluster \
mongo mongod --replSet my-mongo-set 
  
  
*Walkthrough of cluster
 https://www.sohamkamani.com/blog/2016/06/30/docker-mongo-replica-set/
  
  
  
  
  
config = { "_id" : "my-mongo-set", "members" : [ { "_id" : 0, "host" : "mongo1:27017" }, { "_id" : 1, "host" : "mongo2:27017" }, { "_id" : 2, "host" : "mongo3:27017" } ] }
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  