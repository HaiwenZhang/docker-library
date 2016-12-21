FROM aurorasystem/server:latest
MAINTAINER PineWong <pinewong@163.com>

# Node
ADD ./node-v6.9.2-linux-x64.tgz /tmp/
RUN \
  cd /tmp/ && \
  tar -zxf node-v6.9.2-linux-x64.tgz && \
  mv node-v6.9.2-linux-x64 /opt/ && \
  echo 'export PATH=$PATH:/opt/node-v6.9.2-linux-x64/bin' >> ~/etc/profile && \
  source /etc/profile && \
  rm -r /tmp/*