FROM golang:1.14-buster AS build
ENV GOPROXY=https://proxy.golang.org
WORKDIR /go/src/
COPY . .
RUN CGO_ENABLED=0 go build -o /go/bin/hello-from-container .


FROM ubuntu:bionic
RUN mkdir /hello
COPY --from=build /go/bin/hello-from-container /hello/
USER nobody:nogroup
ENTRYPOINT ["/bin/bash", "-c", "./hello/hello-from-container"]
