FROM node:alpine

RUN echo @edge http://nl.alpinelinux.org/alpine/edge/community >> /etc/apk/repositories \
  && apk add --no-cache \
  # chromium dependencies
  nss@edge \
  chromium-chromedriver@edge \
  chromium@edge

USER node

ENV CHROME_BIN /usr/bin/chromium-browser

WORKDIR /usr/src/app
