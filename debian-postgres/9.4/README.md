debian-postgres 9.4
=============
[![](https://images.microbadger.com/badges/image/denmojo/debian-postgres.svg)](https://microbadger.com/images/denmojo/debian-postgres "Get your own image badge on microbadger.com")

This project builds a Docker image with PostgreSQL 9.4 in Debian Jessie.

## Pre-requisites
  * Docker

## Building
  * `docker build [url to raw of the Dockerfile]`

You can also pull it from Docker Hub:
  * `docker pull denmojo/debian-postgres`

## Running

`docker run -d --name=postgres -p 0.0.0.0:32777:5432 denmojo/debian-postgres`

This will run the image container exposing machine port 32777 for connections to the database.

Default user is `produser` with password `produser` in database `prod_db`.

### NOTE: 

Volumes for this build are not specified, making the database and data portable as a single container. To better support portability and separation of duties, an additional docker volume container can be linked to this and uncomment the volume line in the Dockerfile.
