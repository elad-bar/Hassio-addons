ARG BUILD_FROM=hassioaddons/base:7.0.3
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

ARG DAHUA_BRANCH="master"

RUN apk add --no-cache --update argon2-libs php php-json && \
    apk add --no-cache --virtual .build-dependencies git && \
    apk add --update libzip-dev curl-dev && \
    docker-php-ext-install curl && \
    apk del gcc g++ &&\
    rm -rf /var/cache/apk/* && \
    git clone https://github.com/elad-bar/DahuaVTO2MQTT.git --branch ${DAHUA_BRANCH} --depth 1 /app && \
    chmod +x /app/DahuaVTO.php && \
    apk del .build-dependencies

WORKDIR /app

COPY run.sh /app/run.sh
RUN chmod +x /app/run.sh

CMD /app/run.sh
