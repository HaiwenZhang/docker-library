FROM aurorasystem/base-verification:latest
MAINTAINER Aurora System <it@aurora-system>

ADD asiv/* /usr/local/bin/

RUN useradd -ms /bin/bash deploy
RUN chown -R deploy /app
USER deploy
WORKDIR /app
