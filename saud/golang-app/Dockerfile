FROM golang
ADD https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 /usr/bin/dep
ADD . /go/src/github.com/waveywaves/containers-session/golang-app
WORKDIR /go/src/github.com/waveywaves/containers-session/golang-app
RUN chmod +x /usr/bin/dep && dep init && dep ensure --vendor-only && go install github.com/waveywaves/containers-session/golang-app
ENTRYPOINT /go/bin/golang-app
EXPOSE 8080
