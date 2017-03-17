FROM golang:1.8-alpine

RUN mkdir -p /go/src

ADD https://github.com/dgryski/carbonapi/archive/master.zip /tmp/master.zip

# build carbonapi
RUN set -x                                           \
    && apk add --update git                          \
    && cd /go/src                                    \
    && unzip /tmp/master.zip                         \
    && mv /go/src/carbonapi-master /go/src/carbonapi \
    && cd /go/src/carbonapi                          \
    && go-wrapper download                           \
    && go-wrapper install                            \
    && apk del git                                   \
    && rm -f /tmp/master.zip                         \
    && rm -rf /var/cache/apk/*

EXPOSE 8080
ENTRYPOINT [ "/go/bin/carbonapi" ]
