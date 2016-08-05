Jenkins Docker Master
=====================

This repository contains a Jenkins Master installation that has access to
docker and docker-compose commands.

Unlike other Jenkins with Docker images which use Docker in Docker (DIND)
it connects by default with the docker instance on the host and creates sister
containers.

A docker-compose file for this might look like this:
```
version: '2'
services:
  master:
    image: around25/jenkins-docker-master
    restart: always
    ports:
      - 80:8080
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - data:/var/lib/jenkins
    networks:
      default:
        aliases:
          - master.jenkins
```
