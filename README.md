# docker-alpine-elasticsearch
This image is a copy of the https://github.com/docker-library/elasticsearch image. The referenced image was
deprecated in favour of the official [elastic docker image](https://github.com/elastic/elasticsearch-docker) in Elastic Docker registry, see the linked repository.

This repository is for keeping things flexible for future requirements.

It's one of best practices to provide current user's id to the running container.
For this reason docker run accepts the parameter --user. For more details see: https://docs.docker.com/engine/reference/run/#user


# Commands

build:

    docker build -t alpine-elasticsearch --rm=true .

debug:

    docker run -i -t --entrypoint=sh alpine-elasticsearch

run:

    docker run -p 9200:9200 -p 9300:9300 --name es_instance -i -P alpine-elasticsearch

run with mapped data dir:

        docker run -p 9200:9200 -p 9300:9300 --user=$(id -u):$(id -u) -v ~/git/docker-alpine-elasticsearch/data:/usr/share/elasticsearch/data --name es_instance -i -P alpine-elasticsearch


shell login to running container with container-id:

    docker exec -i -t 6617245d262f /bin/bash