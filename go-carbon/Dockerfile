FROM golang:1.8-alpine

RUN mkdir -p /tmp/go-carbon

ENV GOPATH /tmp/go-carbon/_vendor

# build carbonapi
RUN set -x                                                          \
    && cd /tmp/go-carbon                                            \
    && apk add --update git                                         \
    && git clone https://github.com/lomik/go-carbon.git --depth=1 . \
    && git submodule init                                           \
    && git submodule update --recursive                             \
    && go build github.com/lomik/go-carbon                          \
    && mv go-carbon /sbin/                                          \
    && cd /                                                         \
    && apk del git                                                  \
    && rm -f /tmp/$VERSION.zip                                      \
    && rm -rf /tmp/go-carbon                                        \
    && rm -rf /var/cache/apk/*


EXPOSE 2003 2004 7002 7007 2003/udp
ENTRYPOINT [ "/sbin/go-carbon" ]
