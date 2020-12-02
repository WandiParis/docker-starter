# docker-starter

Docker Stack for our internal projects based on Symfony + React.

## Stack

See [docker-compose.yml](docker-compose.yml) for complete configuration.

## Build

```shell
cp docker/db/.env.dist docker/db/.env && cp docker/php/.env.dist docker/php/.env
docker-compose up -d --build
```

## Start

```shell
docker-compose up -d
```

## Close
```shell
docker-compose down
```

## Hosts

| Service       | Host                                      |
|---------------|-------------------------------------------|
| Web           | [localhost](http://localhost)             |
| MailCatcher   | [localhost:1080](http://localhost:1080)   |
| Adminer       | [localhost:8080](http://localhost:8080)   |
| ElasticSearch | [localhost:9200](http://localhost:9200)   |
| Kibana        | [localhost:5601](http://localhost:5601)   |
| RabbitMQ      | [localhost:15672](http://localhost:15672) |
| Mercure       | [localhost:3000](http://localhost:3000)   |