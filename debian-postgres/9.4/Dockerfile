# VERSION: 	0.1
# DESCRIPTION: 	Create the PostgreSQL 9.4 Databasee in a container 
# AUTHOR: 	Dennis Mojado (denmojo@gmail.com)
# COMMENTS: 
#    This file describe how to install PostgreSQL with main 
#    dependencies installed.
# USAGE:
#    # Download PostgreSQL 9.4 Dockerfile
#    
#    # Build PostgreSQL image
#    docker build -t postgresql-9.4 
#
#    docker run -v /var/lib/postgresql/9.4:/var/lib/postgresql/9.4 \ 
#    postgresql-9.4
#
#  
FROM debian:jessie

MAINTAINER Dennis Mojado <denmojo@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -qq && apt-get upgrade -y

RUN apt-get install wget -qq

RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main 9.1" > /etc/apt/sources.list.d/pgdg.list

RUN gpg --keyserver keys.gnupg.net --recv-keys ACCC4CF8

RUN gpg --export --armor ACCC4CF8|apt-key add -

RUN apt-get update

RUN apt-get install postgresql-9.4 postgresql-client-9.4 postgresql-contrib-9.4 -y

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN echo "/etc/init.d/postgresql start && exit 0" > /etc/rc.local

RUN  /etc/init.d/postgresql start &&\
    su postgres -c "psql --command \"CREATE USER produser with password 'produser';\" " &&\
    su postgres -c "psql --command \"CREATE DATABASE prod_db with owner produser;\" "

USER postgres

RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.4/main/pg_hba.conf

RUN echo "listen_addresses='*'" >> /etc/postgresql/9.4/main/postgresql.conf

EXPOSE 5432

# VOLUME  ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]

CMD ["/usr/lib/postgresql/9.4/bin/postgres", "-D", "/var/lib/postgresql/9.4/main", "-c", "config_file=/etc/postgresql/9.4/main/postgresql.conf"]