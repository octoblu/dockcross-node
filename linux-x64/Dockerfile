FROM debian:jessie

RUN apt-get update --fix-missing \
  && apt-get install -y --no-install-recommends \
    ca-certificates \
    build-essential \
    python \
    python2.7 \
    curl \
    libusb-1.0-0-dev \
    libbluetooth-dev \
    libudev-dev \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /opt/node && \
  curl --silent -L https://nodejs.org/dist/v8.1.0/node-v8.1.0-linux-x64.tar.xz | tar --strip 1 -xJ -C /opt/node
RUN mkdir -p /opt/yarn && \
  curl --silent -L https://yarnpkg.com/latest.tar.gz | tar --strip 1 -xz -C /opt/yarn
ENV PATH /opt/yarn/bin:/opt/node/bin:$PATH
RUN mkdir -p /tmp/cache && chmod 777 /tmp/cache
RUN /bin/bash -c 'env HOME=/tmp/cache yarn global add \
 node-gyp \
 node-pre-gyp \
 meshblu-connector-pkger \
 meshblu-connector-uploader-github \
 meshblu-connector-installer-debian'

WORKDIR /work
ENV npm_config_ensure true
