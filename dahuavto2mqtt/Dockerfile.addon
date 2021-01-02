ARG BUILD_FROM=hassioaddons/base:latest
FROM ${BUILD_FROM}

ENV LANG C.UTF-8

ARG DAHUA_BRANCH="master"

WORKDIR /app

RUN apk update && \
    apk upgrade && \
    apk add --no-cache python3 py3-pip py3-setuptools git && \
    pip3 install --upgrade pip --no-cache-dir paho-mqtt requests

RUN git clone https://github.com/elad-bar/DahuaVTO2MQTT.git --branch ${DAHUA_BRANCH} --depth 1 /app


COPY run.sh /app/run.sh
RUN chmod +x /app/run.sh

CMD /app/run.sh