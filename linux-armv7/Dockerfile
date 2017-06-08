FROM dockcross/linux-armv7:latest

RUN dpkg --add-architecture armhf
RUN apt-get update \
  && apt-get install -y \
    libusb-1.0-0-dev:armhf \
    libbluetooth-dev:armhf \
    libudev-dev:armhf

RUN mkdir -p /opt/node && \
  curl --silent -L https://nodejs.org/dist/v8.0.0/node-v8.0.0-linux-armv7l.tar.xz | tar --strip 1 -xJ -C /opt/node
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
