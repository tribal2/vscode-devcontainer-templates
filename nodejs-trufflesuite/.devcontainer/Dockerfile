ARG NODE_VERSION=14.16.0
ARG ALPINE_VERSION=3.13
FROM node:${NODE_VERSION}-alpine${ALPINE_VERSION}

ENV ENV="/root/.profile"
ENV NODE_ENV=development
WORKDIR /app

ARG ENVIRONMENT=development
RUN set -ex \
    && apk --update add --no-cache \
        git \
        bash \
    && rm -rf /var/cache/apk/* \
    # Install node packages
    && npm install --silent --save-dev -g
        truffle \
        ganache-cli \
    # Other setup
    && echo "alias ll='ls -lah'" >> /root/.profile

COPY package*.json ./
RUN npm install --no-progress --ignore-optional

CMD [ "npm", "start" ]
