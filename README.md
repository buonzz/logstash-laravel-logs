# Logstash Laravel Logs

Process Laravel Log files on Logstash and forward to ElasticSearch


### Installation

You will need to have of course an ELK stack running. The easiest way is to use [Vagrant ELK Box](https://github.com/comperiosearch/vagrant-elk-box)

```
git clone https://github.com/comperiosearch/vagrant-elk-box.git
cd vagrant-elk-box
vagrant up
```

once you are done setting it up, clone this repo in the root folder of that vm and login to its ssh
```
git clone https://github.com/buonzz/logstash-laravel-logs.git
```

login to ssh of ELK box
```
vagrant ssh
```

run the sample log file
```
cd /vagrant/logstash-laravel-logs
/opt/logstash/bin/logstash agent -f logstash.conf  < logs/laravel.log
```

This will parse the contents of [laravel.log](https://github.com/buonzz/logstash-laravel-logs/blob/master/logs/laravel.log) sample file. Of course you can replace that file with your actual access log, or specify a different filename.

Once parsed, it will be indexed to ElasticSearch running in the localhost. The default index name is *laravel_logs* To view the indexed data in your browser, just visit this URL:

```
http://localhost:9200/laravel_logs/_search?pretty
```

this will show a result from ElasticSearch, with the tokens of log file broken down to each key.
