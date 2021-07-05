FROM golang:1.16.5-alpine3.14
WORKDIR $GOPATH/src/app/
COPY app.go .
RUN go build ./app.go
# CMD ["./app"]
