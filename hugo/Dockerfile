FROM alpine:latest
MAINTAINER Eric Chastan <eric@chastan.consulting>

ENV HUGO_VERSION=0.18.1
RUN apk add --no-cache --update python3 wget ca-certificates && \
  python3 -m ensurepip && \
  rm -rf /usr/lib/python*/ensurepip /root/.cache /var/cache

RUN  /usr/bin/yes | pip3 --no-cache-dir install --upgrade pip setuptools && \
  /usr/bin/yes | pip3 --no-cache-dir install docutils && \
  for F in /usr/bin/rst2* ; do  mv $F ${F%.py}; done && \
  /usr/bin/yes | pip3 uninstall pip setuptools && \
  rm -rf /usr/lib/python*/ensurepip /root/.cache /var/cache

RUN cd /tmp/ && \
  wget https://github.com/spf13/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && \
  tar xvzf hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && \
  rm -rf hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && \
  mv hugo*/hugo* /usr/bin/hugo && \
  apk del wget ca-certificates  && \
  rm -rf /root/.cache ./var/cache./var/cache

VOLUME /output
