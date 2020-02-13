FROM golang:1.13.7 as builder
COPY . /go/src/github.com/kubernetes-incubator/metrics-server
RUN cd /go/src/github.com/kubernetes-incubator/metrics-server && \
    make _output/amd64/metrics-server

FROM gcr.io/distroless/static@sha256:08322afd57db6c2fd7a4264bf0edd9913176835585493144ee9ffe0c8b576a76

COPY --from=builder /go/src/github.com/kubernetes-incubator/metrics-server/_output/amd64/metrics-server /

ENTRYPOINT ["/metrics-server"]