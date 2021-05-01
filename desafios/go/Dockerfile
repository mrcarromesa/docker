FROM golang:alpine

WORKDIR $GOPATH/src/app/
COPY app.go .
COPY go.mod .
RUN go build -o /go/app

CMD ["/go/app"]