#for optimizing dockerfile here i am using Multi  Stag technique
#ceation of first stag
FROM golang:alpine AS stag1
RUN apk update && apk add --no-cache git
ADD https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 /usr/bin/dep
RUN chmod +x /usr/bin/dep
ADD . /go/src/github.com/waveywaves/containers-session/golang-app
WORKDIR /go/src/github.com/waveywaves/containers-session/golang-app
RUN dep init &&  dep ensure --vendor-only && go install github.com/waveywaves/containers-session/golang-app
# creating new stag and copying binary file from stag1
FROM alpine
COPY --from=stag1 /go/bin/golang-app /go/bin/golang-app
ENTRYPOINT /go/bin/golang-app
EXPOSE 8080
