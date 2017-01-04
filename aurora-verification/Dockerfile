FROM aurorasystem/server:latest
MAINTAINER PineWong <pinewong@163.com>

# Python pip, numpy
ADD ./get-pip.py /tmp
RUN cd /tmp && \
  /usr/local/bin/python3 get-pip.py && \
  pip install numpy
