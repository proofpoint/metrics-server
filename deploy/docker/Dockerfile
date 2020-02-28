FROM golang:1.13.7 as builder
COPY . /go/src/github.com/kubernetes-incubator/metrics-server
RUN cd /go/src/github.com/kubernetes-incubator/metrics-server && \
    make _output/amd64/metrics-server

FROM gcr.io/distroless/static@sha256:23aa732bba4c8618c0d97c26a72a32997363d591807b0d4c31b0bbc8a774bddf

COPY --from=builder /go/src/github.com/kubernetes-incubator/metrics-server/_output/amd64/metrics-server /

ENTRYPOINT ["/metrics-server"]
