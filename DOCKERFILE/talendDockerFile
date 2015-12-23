############################################################
# Dockerfile to build Talend container images
# Based on Ubuntu
###########################################################

# Set the base image to Ubuntu
FROM tomcat:latest

# File Author / Maintainer
MAINTAINER Sébastien Martin

# Update the repository sources list
RUN apt-get update
RUN apt-get -y upgrade

# Install nano
RUN apt-get install -y nano

# Install crontab
RUN apt-get install -y cron

# Création du PATH Talend
RUN mkdir -p /APP/Talend/Builds
RUN mkdir -p /APP/Talend/conf

# Copie des exécutables Talend
COPY Builds /APP/Talend/Builds/
COPY talend.conf /APP/Talend/conf/talend.conf
COPY WebServiceTeamA_0.1.war /usr/local/tomcat/webapps/WebServiceTeamA_0.1.war
COPY cron /APP/Talend/conf/cron

RUN crontab /APP/Talend/conf/cron

CMD service cron start && catalina.sh run
