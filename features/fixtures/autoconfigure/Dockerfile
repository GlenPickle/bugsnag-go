ARG GO_VERSION
FROM golang:${GO_VERSION}-alpine

RUN apk update && apk upgrade && apk add git bash

ENV GOPATH /app

COPY testbuild /app/src/github.com/bugsnag/bugsnag-go
WORKDIR /app/src/github.com/bugsnag/bugsnag-go

RUN go get . ./sessions ./headers ./errors

# Copy test scenarios
COPY ./autoconfigure /app/src/test
WORKDIR /app/src/test

RUN chmod +x run.sh
CMD ["/app/src/test/run.sh"]
