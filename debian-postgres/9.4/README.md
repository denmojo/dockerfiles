debian-postgres 9.4
=============

This project builds a Docker image with PostgreSQL 9.4 in Debian Jessie.

## Pre-requisites
  * Docker

## Building
  * `docker build [url to raw of the Dockerfile]`

You can also pull it from Docker Hub:
  * `docker pull denmojo/debian-postgres`

## Running

`docker run -p 0.0.0.0:32777:5432 --name=postgres denmojo/debian-postgres`

This will run the image container exposing machine port 32777 for connections to the database.

Default user is `produser` with password `produser` in database `prod_db`.
