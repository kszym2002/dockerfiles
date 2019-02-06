FROM golang as builder
RUN apt update && apt install git -y 
RUN go get -u -d github.com/rc452860/vnet/...
RUN  go build /usr/local/go/src/github.com/rc452860/vnet/cmd/server/server.go --ldflags '-linkmode external -extldflags "-static"'

FROM alpine:3.9 
COPY --from=builder /usr/local/go/src/github.com/rc452860/vnet/cmd/server/ /vnet
WORKDIR /vnet

CMD ./server
