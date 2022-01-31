---
description: >-
  You need Twake for more than 500 users ? You want to leverage ScyllaDB and
  ElasticSearch replication ? You are in the right place !
---

# 🎡 Scale with Twake

Scaling with Twake is possible if you install Twake with RabbitMQ, Redis, ElasticSearch and ScyllaDB.

```
git clone https://github.com/TwakeApp/Twake.git
cd Twake/twake

cp -n docker-compose.yml.dist.onpremise docker-compose.yml
cp -nR default-configuration/ configuration/

docker-compose pull

docker-compose up -d scylladb
sleep 5m #Wait scylladb to startup
docker-compose up -d php rabbitmq
sleep 10m #Wait php to create tables in scylladb

docker-compose up -d
```

> To run ElasticSearch (optional, but enabled by default in the Twake docker-compose) you must increase the max\_map\_count of your system: [https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#\_set\_vm\_max\_map\_count\_to\_at\_least\_262144](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#\_set\_vm\_max\_map\_count\_to\_at\_least\_262144)
>
> To fix an other bug with ElasticSearch container, you must also run this command: `chmod 777 ./docker-data/es_twake` (create the folder if it doesn't exists in your docker-compose.yml folder)

Twake will be running on port 8000 🎉
