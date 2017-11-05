From golang:1.9

MAINTAINER mmm888

RUN apt-get update; apt-get -y install vim; git clone https://github.com/mmm888/exchange-api-go ${GOPATH}/src/github.com/mmm888/exchange-api-go
WORKDIR ${GOPATH}/src/github.com/mmm888/exchange-api-go
COPY secret.go ${GOPATH}/src/github.com/mmm888/exchange-api-go/
RUN go get -u github.com/golang/dep/cmd/dep; dep ensure

WORKDIR ${GOPATH}/src/github.com/mmm888/exchange-api-go/cmd/goanda
RUN go build .; mv goanda ${GOPATH}/bin

WORKDIR ${GOPATH}

CMD goanda influxdb init && goanda influxdb past && goanda influxdb streaming
