FROM centos:7
MAINTAINER PineWong <pinewong@163.com>

# Oracle Java 1.8
RUN \
  curl -O http://download.oracle.com/otn-pub/java/jdk/8u111-b14/jdk-8u111-linux-x64.rpm && \
  rpm -ivh jdk-8u111-linux-x64.rpm && \
  echo '#!/bin/bash' > /etc/profile.d/java.sh && \
  echo 'JAVA_HOME=/usr/java/jdk1.8.0_111/' >> /etc/profile.d/java.sh && \
  echo 'PATH=$JAVA_HOME/bin:$PATH' >> /etc/profile.d/java.sh && \
  echo 'export PATH JAVA_HOME' >> /etc/profile.d/java.sh && \
  echo 'export CLASSPATH=.' >> /etc/profile.d/java.sh && \
  chmod +x /etc/profile.d/java.sh && \
  source /etc/profile.d/java.sh

# Dependence
RUN apt-get update && apt-get install -y maven git libtool autoconf build-essential pkg-config gettext

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

# clean
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Project
RUN mkdir -p /app/log && mkdir -p /app/tmp
WORKDIR /app
