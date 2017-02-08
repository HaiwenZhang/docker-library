FROM aurorasystem/server:latest
MAINTAINER Aurora System <it@aurora-system.com>

# Node
RUN \
  curl --silent --location https://rpm.nodesource.com/setup_6.x | bash - && \
  yum -y install bzip2 nodejs && \
  yum clean all
