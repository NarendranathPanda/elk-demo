# Check the Logs for filebeat 
```
journalctl -u filebeat.service -f
```
# Check the logs for logstash 

```
journalctl -u logstash.service -f
```

# Check the indices 
```
 curl -v http://localhost:9200/_cat/indices
```

# Configure the index at kibana 
```
http://<localhost:5601>/app/kibana#/management/elasticsearch/index_management/indices
```
# If you want to run production grade elastic 
```
https://www.elastic.co/guide/en/elasticsearch/reference/current/bootstrap-checks.html
```
# Setting Single Node Elasticsearch 
```
https://www.elastic.co/guide/en/elasticsearch/reference/current/bootstrap-checks.html#single-node-discovery
```
# If you want to pass extra JAVA OPTS 
```
edit /etc/default/elasticsearch
https://www.elastic.co/guide/en/elasticsearch/reference/current/setting-system-settings.html#systemd
```


