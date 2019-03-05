FROM golang as builder
RUN apt update && apt install git -y 
RUN git clone https://github.com/rc452860/vnet.git /usr/local/go/src/github.com/rc452860/vnet
RUN  cd  /usr/local/go/src/github.com/rc452860/vnet/cmd/server/ && \
    go build --ldflags '-linkmode external -extldflags "-static"'

FROM alpine:3.8
ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}

RUN apk upgrade --update \
    && apk add bash tzdata \
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /var/cache/apk/*
COPY --from=builder /usr/local/go/src/github.com/rc452860/vnet/cmd/server/ /vnet
WORKDIR /vnet

CMD ./server
