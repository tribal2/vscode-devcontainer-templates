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
    && npm install --silent --save-dev -g \
        typescript \
    # Other setup
    && echo "alias ll='ls -lahvF --group-directories-first'" \
        | tee -a /root/.profile /root/.bashrc

COPY package*.json ./
RUN npm install --no-progress --ignore-optional

CMD [ "npm", "start" ]
