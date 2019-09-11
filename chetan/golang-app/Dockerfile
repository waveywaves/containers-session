# Optimized the image to 11.8 MB using multi stage builds

# First stage to produce the binary executable file of the golang app
FROM golang:1.10-alpine3.8 AS first-stage
RUN apk add --no-cache git
ADD https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 /usr/bin/dep
RUN chmod +x /usr/bin/dep
COPY . /go/src/github.com/waveywaves/containers-session/golang-app
WORKDIR /go/src/github.com/waveywaves/containers-session/golang-app
RUN dep init \
    && dep ensure --vendor-only \
    && go install github.com/waveywaves/containers-session/golang-app
# Build the golang app to produce the binary file
RUN go build -o /go/bin/golang-app


# Create a new base image with alpine
FROM alpine:3.8
# Copy the binary executable file from the first stage
COPY --from=first-stage /go/bin/golang-app /go/bin/golang-app
EXPOSE 8080
ENTRYPOINT /go/bin/golang-app
