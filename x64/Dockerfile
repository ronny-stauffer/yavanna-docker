# Pull base image
#FROM debian:jessie
FROM java:8-jre
MAINTAINER Ronny Stauffer <ronny.stauffer@wir-entwickeln.ch>

RUN ln -s -f /bin/bash /bin/sh

# Install dependencies
# (Deletes Debian package lists at the end.)
RUN apt-get update && \
    apt-get install -y \
    git mosquitto mosquitto-clients \
    --no-install-recommends; \
    rm -rf /var/lib/apt/lists/*

# Define working directory
WORKDIR /yavanna

ADD resources/openhab.tar openhab/
ADD resources/run run

RUN chmod +x run openhab/start.sh

# Define commonly used JAVA_HOME variable
#ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-armhf

# Define default command
#CMD ["bash"]
CMD ["bash", "-c", "./run"]

VOLUME /yavanna/openhab/configurations

EXPOSE 1883 9123 49152 8080
