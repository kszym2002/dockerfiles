FROM frolvlad/alpine-glibc
ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}

RUN apk upgrade --update \
&& apk add tzdata 

COPY ./vnet /vnet
RUN chmod +x /vnet/vnet
RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
&& echo ${TZ} > /etc/timezone 
WORKDIR /vnet

CMD ./vnet
