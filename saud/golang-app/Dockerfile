#FROM golang
FROM golang:1.13.0-alpine AS build

# Utils, tools
# Layer is built when packages are updated
RUN apk add --no-cache git
#RUN go get github.com/golang/dep/cmd/dep

# Copy the project
ADD https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 /usr/bin/dep
#ADD . /go/src/github.com/waveywaves/containers-session/golang-app
COPY . /go/src/github.com/waveywaves/containers-session/golang-app

# set dir & install project
WORKDIR /go/src/github.com/waveywaves/containers-session/golang-app
#RUN chmod +x /usr/bin/dep && dep init && dep ensure --vendor-only && go install github.com/waveywaves/containers-session/golang-app
RUN chmod +x /usr/bin/dep && \
dep init && \
dep ensure --vendor-only && \
go install github.com/waveywaves/containers-session/golang-app

# multi stage image, create a new alpine base layer
FROM alpine
COPY --from=build /go/bin /go/bin

ENTRYPOINT /go/bin/golang-app
EXPOSE 8080
