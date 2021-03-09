# Twofishes is not owned or packaged by us
# and the full installation instructions can
# be found at their location. Twofishes
# location service is used by the OMAR/O2 UI
#FROM REGISTRY_URI/o2-base:TAG_PLACEHOLDER
FROM centos:centos7
MAINTAINER RadiantBlue Technologies radiantblue.com
LABEL com.radiantblue.version="0.1"\
      com.radiantblue.description="Twofishes is\
      not owned or packaged by us and the full\
      installation instructions can be found at\
      their location. Twofishes location service\
      is used by the OMAR/O2 UI."\
      com.radiantblue.source=""\
      com.radiantblue.classification="UNCLASSIFIED"
RUN useradd -u 1001 -r -g 0 -d $HOME -s /sbin/nologin -c 'Default Application User' omar && \
    mkdir /usr/share/omar && \
    yum -y install java-11-openjdk-devel && \
    yum -y install wget && yum -y install unzip && \
    cd  /usr/share/omar && \
    wget https://s3.amazonaws.com/ossimlabs/dependencies/twofishes/server-assembly-0.84.9.jar && \
    wget https://s3.amazonaws.com/ossimlabs/dependencies/twofishes/2015-03-05.zip && \
    unzip 2015-03-05.zip && rm 2015-03-05.zip && \
    yum -y update

# We need to do this because twofishes crashes without it:
# http://jaredmarkell.com/docker-and-locales/
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8


USER 1001
WORKDIR /usr/share/omar

CMD java -server -Xmx256m -Xmx4096m -jar /usr/share/omar/server-assembly-0.84.9.jar --port 8080 --hfile_basepath /usr/share/omar/2015-03-05-20-05-30.753698

EXPOSE 8080 8081 8082 8083
