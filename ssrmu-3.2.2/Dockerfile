FROM python:3.7.1-alpine3.8
MAINTAINER FAN VINGA<fanalcest@gmail.com> \
           EasonSummer<kszym2002@gmail.com>

RUN  apk --no-cache add \
                        curl \
                        libsodium-dev \
                        openssl-dev \
                        udns-dev \
                        mbedtls-dev \
                        pcre-dev \
                        libev-dev \
                        libtool \
                        libffi-dev            && \
     apk --no-cache add --virtual .build-deps \
                        git \
                        tar \
                        make \
                        autoconf \
                        automake \
                        build-base \
                        linux-headers         && \
     ln -s /usr/bin/python3 /usr/bin/python   && \
     ln -s /usr/bin/pip3    /usr/bin/pip     

COPY ./shadowsocks  /root/shadowsocks

RUN  cd  /root/shadowsocks                    && \
     pip install -r requestment.txt         && \
     rm -rf ~/.cache && touch /etc/hosts.deny && \
     apk del --purge .build-deps



CMD python /root/shadowsocks/server.py
