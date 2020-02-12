FROM golang:1.13.7 as builder
COPY . /go/src/github.com/kubernetes-incubator/metrics-server
RUN cd /go/src/github.com/kubernetes-incubator/metrics-server && \
    make _output/amd64/metrics-server

FROM gcr.io/distroless/static:latest

COPY --from=builder /go/src/github.com/kubernetes-incubator/metrics-server/_output/amd64/metrics-server /

ENTRYPOINT ["/metrics-server"]