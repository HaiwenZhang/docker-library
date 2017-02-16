FROM aurorasystem/server:latest
MAINTAINER Aurora System <it@aurora-system>

# Python3 and MKL
RUN \
  yum install -y epel-release && yum install -y python34 && yum remove -y epel-release && yum clean all && \
  ln -s /usr/bin/python3 /usr/local/bin/python3 &&\ yum install -y fftw

# Python pip, numpy
ADD ./get-pip.py /tmp
RUN cd /tmp && \
  /usr/local/bin/python3 get-pip.py && \
  pip install numpy

ADD mkl_so/* /usr/local/lib/
