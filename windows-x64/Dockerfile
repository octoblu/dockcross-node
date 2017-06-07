FROM dockcross/windows-x64:latest

RUN apt-get update \
  && apt-get install -y \
    unzip

RUN mkdir -p /opt/node \
  && curl --silent -L -O https://nodejs.org/dist/v7.6.0/node-v7.6.0-win-x64.zip \
  && unzip node-v7.6.0-win-x64.zip \
  && mv node-v7.6.0-win-x64/* /opt/node \
  && rm -rf node-v7.6.0-win-x64*
