FROM aurorasystem/server:latest
MAINTAINER PineWong <pinewong@163.com>

# Node
RUN \
  curl --silent --location https://rpm.nodesource.com/setup_6.x | bash - && \
  yum -y install bzip2 nodejs && \
  yum clean all
