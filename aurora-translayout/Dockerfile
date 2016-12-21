FROM aurorasystem/server:latest
MAINTAINER PineWong <pinewong@163.com>

# Node
RUN \
  curl --silent --location https://rpm.nodesource.com/setup_6.x | bash - && \
  yum -y install nodejs && \
  yum clean all
RUN mkdir -p /app/TransLayout/SVGToPNG/
ADD ./package.json /app/TransLayout/SVGToPNG/
RUN cd /app/TransLayout/SVGToPNG/ && npm install
