FROM node:8.1-alpine

ADD app/package.json /tmp/package.json
RUN cd /tmp && npm install
RUN mkdir -p /usr/local/bos-web && cp -a /tmp/node_modules /usr/local/bos-web

RUN apk add --no-cache git && npm install -g bower && npm install -g pm2
ADD app/bower.json /tmp/bower.json
RUN cd /tmp && bower install --allow-root
RUN mkdir -p /usr/local/bos-web && cp -a /tmp/bower_components /usr/local/bos-web

WORKDIR /usr/local/bos-web
ADD app /usr/local/bos-web

CMD [ "pm2-docker", "index.js" ]