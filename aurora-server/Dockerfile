FROM centos:7
MAINTAINER PineWong <pinewong@163.com>

# Dependence
RUN yum update && yum install -y wget maven git libtool autoconf build-essential pkg-config gettext

# Oracle Java 1.8
RUN \
  cd /opt/ && \
  wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u111-b14/jdk-8u111-linux-x64.tar.gz" && \
  tar -xzf jdk-8u111-linux-x64.tar.gz && \

  cd /opt/jdk1.8.0_111/ && \
  alternatives --install /usr/bin/java java /opt/jdk1.8.0_111/bin/java 2 && \
  alternatives --config java && \

  alternatives --install /usr/bin/jar jar /opt/jdk1.8.0_111/bin/jar 2 && \
  alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_111/bin/javac 2 && \
  alternatives --set jar /opt/jdk1.8.0_111/bin/jar && \
  alternatives --set javac /opt/jdk1.8.0_111/bin/javac && \
  java -version

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
RUN yum clean && rm -rf /var/lib/apt/lists/*

# Project
RUN mkdir -p /app/log && mkdir -p /app/tmp
WORKDIR /app
