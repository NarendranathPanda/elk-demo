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

#Configure the index at kibana 
```
http://<localhost:5601>/app/kibana#/management/elasticsearch/index_management/indices
```


