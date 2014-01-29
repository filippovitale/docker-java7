# Oracle Java7

```
FROM ubuntu
MAINTAINER Filippo Vitale @filippovitale

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list.d/ubuntuarchive.list
RUN apt-get install -qy python-software-properties
RUN add-apt-repository ppa:webupd8team/java
RUN apt-get -qy update

RUN echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections
RUN apt-get install -qy oracle-java7-installer
RUN echo JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::") >> /etc/environment
```
