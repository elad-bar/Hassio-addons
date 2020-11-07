ARG BUILD_FROM=hassioaddons/base:8.0.5

# hadolint ignore=DL3006
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

ARG DAHUA_BRANCH="master"

RUN apk add --no-cache --update argon2-libs php php-json php-curl && \
    apk add --no-cache --virtual .build-dependencies git curl && \
    git clone https://github.com/elad-bar/DahuaVTO2MQTT.git --branch ${DAHUA_BRANCH} --depth 1 /app && \
    chmod +x /app/DahuaVTO.php && \
    apk del .build-dependencies

RUN which curl

WORKDIR /app

COPY run.sh /app/run.sh
RUN chmod +x /app/run.sh

CMD /app/run.sh