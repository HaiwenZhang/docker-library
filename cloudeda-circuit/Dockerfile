# MAINTAINER        pinewong <pinewong@163.com>
# DOCKER-VERSION    1.12.6
#
# Dockerfile for the ServiceController of Aurora Platform.
# Usage: docker pull pinewong/aurora-service

FROM debian:jessie
MAINTAINER pinewong <pinewong@163.com>

# Oracle Java 1.8
RUN \
    echo "===> add webupd8 repository..."  && \
    echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee /etc/apt/sources.list.d/webupd8team-java.list  && \
    echo "deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" | tee -a /etc/apt/sources.list.d/webupd8team-java.list  && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886  && \
    apt-get update  && \
    \
    \
    echo "===> install Java"  && \
    echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections  && \
    echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections  && \
    DEBIAN_FRONTEND=noninteractive  apt-get install -y --force-yes oracle-java8-installer oracle-java8-set-default  && \
    \
    \
    echo "===> clean up..."  && \
    rm -rf /var/cache/oracle-jdk8-installer  && \
    apt-get clean  && \
    rm -rf /var/lib/apt/lists/*

# Dependence
RUN apt-get update
RUN apt-get install -y maven git libtool autoconf build-essential pkg-config gettext

# RUN sed -i '$d' /etc/maven/settings.xml
# RUN echo -e "  <localRepository>/app/maven</localRepository>\n</settings>" >> /etc/maven/settings.xml

WORKDIR /tmp
RUN git clone https://github.com/zeromq/libzmq.git
WORKDIR /tmp/libzmq/
RUN ./autogen.sh
RUN ./configure
RUN make -j 4
RUN make check
RUN make install
RUN ldconfig

WORKDIR /tmp
RUN git clone https://github.com/zeromq/jzmq.git
WORKDIR /tmp/jzmq/jzmq-jni/
RUN ./autogen.sh
RUN ./configure
RUN make
RUN make install
WORKDIR /tmp/jzmq/
RUN mvn package
