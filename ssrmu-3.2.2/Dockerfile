FROM alpine:3.9
MAINTAINER FAN VINGA<fanalcest@gmail.com> \
           EasonSummer<kszym2002@gmail.com>

ENV DNS_1=1.0.0.1                 \
    DNS_2=8.8.8.8                 

ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}

RUN apk upgrade --update \
&& apk add tzdata 

RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
&& echo ${TZ} > /etc/timezone 

WORKDIR /root/shadowsocks

RUN  apk --no-cache add \
                        curl \
                        git \
                        libintl \
                        python3-dev \
                        libsodium-dev \
                        openssl-dev \
                        udns-dev \
                        mbedtls-dev \
                        pcre-dev \
                        libev-dev \
                        libtool \
                        libffi-dev            && \
     apk --no-cache add --virtual .build-deps \
                        tar \
                        make \
                        gettext \
                        py3-pip \
                        autoconf \
                        automake \
                        build-base \
                        linux-headers         && \
     ln -s /usr/bin/python3 /usr/bin/python   && \
     ln -s /usr/bin/pip3    /usr/bin/pip      && \
     cp  /usr/bin/envsubst  /usr/local/bin/   && \
     git clone https://github.com/LEE-Blog/shadowsocksr.git /root/shadowsocks && \
     pip install --upgrade pip                && \
     pip install cymysql                      && \        
     rm -rf ~/.cache && touch /etc/hosts.deny && \
     apk del --purge .build-deps
     



CMD echo -e "${DNS_1}\n${DNS_2}\n" > dns.conf  && \
    python server.py

