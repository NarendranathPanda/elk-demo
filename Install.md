# Host Information 
```
lsb_release -a
--------------------
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
```

# Install java 
```
sudo add-apt-repository -y ppa:webupd8team/java
sudo apt-get update
sudo apt-get -y install oracle-java8-installer
----------------------
java -version
openjdk version "1.8.0_252"
OpenJDK Runtime Environment (build 1.8.0_252-8u252-b09-1~18.04-b09)
OpenJDK 64-Bit Server VM (build 25.252-b09, mixed mode)
```

# Install Elastic Search
ref : https://www.elastic.co/guide/en/elasticsearch/reference/7.8/deb.html#deb-repo
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
sudo apt-get update && sudo apt-get install elasticsearch

sudo vi /etc/elasticsearch/elasticsearch.yml
---------
network.host: localhost
---------
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable elasticsearch.service
----------------------------
 elasticsearch.service - Elasticsearch
   Loaded: loaded (/usr/lib/systemd/system/elasticsearch.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2020-06-20 09:34:29 UTC; 8min ago
     Docs: https://www.elastic.co
 Main PID: 18072 (java)
    Tasks: 64 (limit: 4704)
   CGroup: /system.slice/elasticsearch.service
           ├─18072 /usr/share/elasticsearch/jdk/bin/java -Xshare:auto -Des.networkaddress.cache.ttl=60 -Des.networkaddress.cache.negative.ttl=10 -XX:+Alw
           └─18266 /usr/share/elasticsearch/modules/x-pack-ml/platform/linux-x86_64/bin/controller

-----------------------------
netstat -tnlp | grep 9200
-----------------------------
tcp6       0      0 127.0.0.1:9200          :::*                    LISTEN      18072/java
-----------------------------

curl -X GET "localhost:9200/?pretty"
output:

{
  "name" : "ubuntu-elk",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "INK-VT0kRBGy2pxvAAWwwYUg",
  "version" : {
    "number" : "7.8.0",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "75731464395644ea9a1dc2fecd26d1a43856725e65",
    "build_date" : "2020-06-14T19:35:50.234439Z",
    "build_snapshot" : false,
    "lucene_version" : "8.5.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}


```
# Install Kibana 
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
sudo apt-get update && sudo apt-get install kibana
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable kibana.service
sudo systemctl start kibana.service

netstat -tnlp | grep 5601
-----------------------------
tcp        0      0 127.0.0.1:5601          0.0.0.0:*               LISTEN      23723/node
-----------------------------

```



# Install nginx
# Install Logstash
# Install FileBeats

