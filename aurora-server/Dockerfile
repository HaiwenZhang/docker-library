FROM centos:7
MAINTAINER PineWong <pinewong@163.com>

# Dependence
RUN yum update && yum install -y wget

# Oracle Java 1.8
RUN \
  cd /tmp && \
  wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.rpm && \
  yum localinstall -y jdk-8u102-linux-x64.rpm && \
  echo 'export JAVA_HOME=/usr/java/jdk1.8.0_102/' >> /etc/profile && \
  echo 'export JRE_HOME=/usr/java/jdk1.8.0_102/jre' >> /etc/profile && \
  echo 'export PATH=$PATH:$HOME/bin:$JAVA_HOME/bin' >> /etc/profile && \
  source /etc/profile && \
  rm /tmp/jdk-8u102-linux-x64.rpm

RUN yum update && yum install -y maven git libtool autoconf build-essential pkg-config gettext

# Zeromq
RUN \
  cd /tmp && \
  git clone https://github.com/zeromq/libzmq.git && \
  cd /tmp/libzmq/ && \
  ./autogen.sh && \
  ./configure && \
  make -j 4 && \
  make check && \
  make install && \
  ldconfig

# jzmq
RUN \
  cd /tmp && \
  git clone https://github.com/zeromq/jzmq.git && \
  cd /tmp/jzmq/jzmq-jni/ && \
  ./autogen.sh && \
  ./configure && \
  make && \
  make install && \
  cd /tmp/jzmq/ && \
  mvn package

# Project
RUN mkdir -p /app/log && mkdir -p /app/tmp
WORKDIR /app
