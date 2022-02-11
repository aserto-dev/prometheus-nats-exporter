FROM golang:1.16 AS build
COPY . /go/src/prometheus-nats-exporter
WORKDIR /go/src/prometheus-nats-exporter
RUN make prometheus-nats-exporter.docker

FROM alpine:latest
RUN apk add --no-cache ca-certificates

COPY --from=build /go/src/prometheus-nats-exporter/prometheus-nats-exporter.docker /prometheus-nats-exporter

EXPOSE 7777
