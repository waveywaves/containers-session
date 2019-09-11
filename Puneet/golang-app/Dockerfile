#Get the base image at the first stage
FROM golang:alpine AS builder	

#update the alpine libraries.		
RUN apk update && apk add --no-cache git	

#
ADD https://github.com/golang/dep/releases/download/v0.4.1/dep-linux-amd64 /usr/bin/dep		

#Allow the execution permissions
RUN chmod +x /usr/bin/dep			

#Copy ti the local machine
COPY . /go/src/github.com/waveywaves/containers-session/golang-app		

#Sets the working directory
WORKDIR /go/src/github.com/waveywaves/containers-session/golang-app
RUN dep init && dep ensure --vendor-only && go install github.com/waveywaves/containers-session/golang-app

#Builds the binary 
RUN go build -o /go/bin/golang-app

#Second Stage
FROM alpine				

#Copy the binary from the first stage
COPY --from=builder /go/bin/golang-app /go/bin/golang-app 		
ENTRYPOINT /go/bin/golang-app
EXPOSE 8080



