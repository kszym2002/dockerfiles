FROM python:3.7.1-alpine3.8
MAINTAINER FAN VINGA<fanalcest@gmail.com>

RUN  apk --no-cache add \
                        curl \
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
                        git \
                        tar \
                        make \
                        py3-pip \
                        autoconf \
                        automake \
                        build-base \
                        linux-headers         && \
     ln -s /usr/bin/python3 /usr/bin/python   && \
     ln -s /usr/bin/pip3    /usr/bin/pip      && \
     t clone -b manyuser https://github.com/SakuraSa233/shadowsocks.git "/root/shadowsocks" --depth 1 && \
     cd  /root/shadowsocks                    && \
     pip install -r requirements.txt          && \
     rm -rf ~/.cache && touch /etc/hosts.deny && \
     apk del --purge .build-deps

WORKDIR /root/shadowsocks

CMD python /root/shadowsocks/server.py
