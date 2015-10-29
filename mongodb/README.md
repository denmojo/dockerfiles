mongodb
=============

This project builds a Docker image with mongodb in Debian Jessie.

## Pre-requisites
  * Docker

## Building
  * create a volume container found in data_container directory
  * `docker build [url to raw of the Dockerfile]`

You can also pull it from Docker Hub:
  * `docker pull denmojo/mongodb`

## Running

`docker run -d -p :27017 --volumes-from data_container --name mongodb mongodb_$BUILD_ID`

This will run the image container exposing machine port 27017 for connections to the database.
