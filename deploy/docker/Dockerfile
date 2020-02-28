FROM golang:1.13.7 as builder
COPY . /go/src/github.com/kubernetes-incubator/metrics-server
RUN cd /go/src/github.com/kubernetes-incubator/metrics-server && \
    make _output/amd64/metrics-server

FROM gcr.io/distroless/static@sha256:c6d5981545ce1406d33e61434c61e9452dad93ecd8397c41e89036ef977a88f4

COPY --from=builder /go/src/github.com/kubernetes-incubator/metrics-server/_output/amd64/metrics-server /

ENTRYPOINT ["/metrics-server"]
