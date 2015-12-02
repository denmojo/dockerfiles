neo4j
=============

This project builds a Docker image with Neo4j 2.3.1 

## Pre-requisites
  * Docker

## Building
  * create a volume container found in `data_container` in parent directory
  * `docker build [url to raw of the Dockerfile]`

You can also pull it from Docker Hub:
  * `docker pull denmojo/neo4j`

## Running

Assuming you start and name data container as "data_container":

`docker run -d -p 7474:7474 --volumes-from data_container --name neo4j $BUILD_ID`

