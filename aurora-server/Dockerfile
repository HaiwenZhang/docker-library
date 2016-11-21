FROM centos:7
MAINTAINER PineWong <pinewong@163.com>

# Dependence
RUN yum update && yum install -y wget gcc automake autoconf libtool make gcc-c++ gtk2 libXtst && yum clean all

# Oracle Java 1.8
RUN \
  cd /tmp && \
  wget -O jdk.rpm --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.rpm && \
  yum localinstall -y jdk.rpm && \
  echo 'export JAVA_HOME=/usr/java/jdk1.8.0_102/' >> /etc/profile && \
  echo 'export JRE_HOME=/usr/java/jdk1.8.0_102/jre' >> /etc/profile && \
  echo 'export PATH=$PATH:$HOME/bin:$JAVA_HOME/bin' >> /etc/profile && \
  source /etc/profile && \
  rm /tmp/*

# Zeromq
RUN \
  cd /tmp && \
  wget -O zeromq.tar.gz https://github.com/zeromq/zeromq3-x/releases/download/v3.2.5/zeromq-3.2.5.tar.gz && \
  tar -zxf zeromq.tar.gz && cd zeromq/ && \
  ./configure && make && make install && \
  rm /tmp/*

# jzmq
RUN \
  cd /tmp && \
  wget -O jzmq.tar.bz https://github.com/zeromq/jzmq/archive/v3.1.0.tar.gz && \
  tar -zxf jzmq.tar.bz && cd jzmq/ && \
  ./autogen.sh && ./configure && make && make install && \
  rm /tmp/*

# Translayout need
RUN mkdir -p /usr/share/fonts/wqy-microhei
ADD ./wqy-microhei.ttc /usr/share/fonts/wqy-microhei/wqy-microhei.ttc
RUN fc-cache /usr/share/fonts/wqy-microhei

# Project
RUN mkdir -p /app/log && mkdir -p /app/tmp
WORKDIR /app
