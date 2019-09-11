
FROM golang:1.10-alpine3.8 AS first-stage
RUN apk add --no-cache git
ADD https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 /usr/bin/dep
RUN chmod +x /usr/bin/dep
COPY . /go/src/github.com/waveywaves/containers-session/golang-app
WORKDIR /go/src/github.com/waveywaves/containers-session/golang-app
RUN dep init \
    && dep ensure --vendor-only \
    && go install github.com/waveywaves/containers-session/golang-app
RUN go build -o /go/bin/golang-app

FROM alpine:3.8
COPY --from=first-stage /go/bin/golang-app /go/bin/golang-app
ENTRYPOINT /go/bin/golang-app
EXPOSE 8080

