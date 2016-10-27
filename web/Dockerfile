# MAINTAINER        pinewong <pinewong@163.com>
# DOCKER-VERSION    1.12.6
#
# Dockerfile for the auroraWS of Aurora Platform.
# Usage: docker pull pinewong/aurora-web

FROM ruby:2.3.0
MAINTAINER pinewong <pinewong@163.com>

# Dependence
RUN apt-get update
RUN apt-get install -y nodejs libzmq3-dev
RUN gem install bundler --no-doc --no-ri
