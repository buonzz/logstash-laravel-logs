# Logstash Laravel Logs

Process Laravel Log files on Logstash and forward to ElasticSearch

### Running

```
logstash agent -f logstash.conf < logs/laravel.log
```