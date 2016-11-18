FROM centos:7
MAINTAINER PineWong <pinewong@163.com>

# Oracle Java 1.8
RUN \
  yum update && yum install -y wget && \
  cd /tmp && \
  wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.rpm && \
  yum localinstall -y jdk-8u102-linux-x64.rpm && \
  echo 'export JAVA_HOME=/usr/java/jdk1.8.0_102/' >> /etc/profile && \
  echo 'export JRE_HOME=/usr/java/jdk1.8.0_102/jre' >> /etc/profile && \
  echo 'export PATH=$PATH:$HOME/bin:$JAVA_HOME/bin' >> /etc/profile && \
  source /etc/profile && \
  rm /tmp/jdk-8u102-linux-x64.rpm

# Zeromq
RUN \
  yum update && yum install -y wget gcc automake autoconf libtool make gcc-c++ && \
  cd /tmp && \
  wget https://github.com/zeromq/zeromq3-x/releases/download/v3.2.5/zeromq-3.2.5.tar.gz && \
  tar -zxf zeromq-3.2.5.tar.gz && cd zeromq-3.2.5/ && \
  ./configure && make && make install

# jzmq
RUN \
  cd /tmp && \
  cd /tmp && \
  wget -O jzmq-3.1.0.tar.bz https://github.com/zeromq/jzmq/archive/v3.1.0.tar.gz && \
  tar -zxf jzmq-3.1.0.tar.bz && cd jzmq-3.1.0/ && \
  ./autogen.sh && ./configure && make && make install

# Project
RUN mkdir -p /app/log && mkdir -p /app/tmp
WORKDIR /app
