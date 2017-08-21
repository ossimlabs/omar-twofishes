# OMAR Twofishes

## Dockerfile
```
FROM omar-base
USER root
RUN yum -y install java-1.8.0-openjdk-devel
RUN yum -y install wget
RUN yum -y install unzip
RUN cd  /home/omar
RUN wget https://s3.amazonaws.com/ossimlabs/dependencies/twofishes/server-assembly-0.84.9.jar
RUN wget https://s3.amazonaws.com/ossimlabs/dependencies/twofishes/2015-03-05.zip
RUN unzip 2015-03-05.zip && rm 2015-03-05.zip
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8
USER 1001
WORKDIR /home/omar
CMD java -server -Xmx256m -Xmx4096m -jar /home/omar/server-assembly-0.84.9.jar --port 8080 --hfile_basepath /home/omar/2015-03-05-20-05-30.753698
EXPOSE 8080 8081 8082 8083
```
Ref: [omar-base](../../../omar-ossim-base/docs/install-guide/omar-base/)
