FROM golang as builder
RUN apt update && apt install git -y 
RUN git clone https://github.com/rc452860/vnet.git /usr/local/go/src/github.com/rc452860/vnet
RUN  cd  /usr/local/go/src/github.com/rc452860/vnet/cmd/server/ && \
    go build --ldflags '-linkmode external -extldflags "-static"'

FROM alpine:3.8 
COPY --from=builder /usr/local/go/src/github.com/rc452860/vnet/cmd/server/ /vnet
WORKDIR /vnet

CMD ./server
