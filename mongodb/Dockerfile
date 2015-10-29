FROM ubuntu
# Installation of MongoDB:
# Import MongoDB public GPG key AND create a MongoDB list file
RUN apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv 7F0CEB10
RUN echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | tee       /etc/apt/sources.list.d/10gen.list

# Update apt-get sources AND install MongoDB
RUN apt-get update && apt-get install -y mongodb-org

# Expose port 27017 from the container to the host
EXPOSE 27017

# Set the mongod daemon as entry-point application
ENTRYPOINT /usr/bin/mongod
