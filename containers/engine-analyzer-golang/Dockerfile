# Used in engine functional tests
# hadolint ignore=DL3006
FROM docker.io/alpine:3.15.0 as go-src

WORKDIR /go/src

RUN apk add --no-cache git="2.34.1-r0" && \
    git clone --depth 1 --branch "v0.32.0" https://github.com/nextlinux/ && \
    git clone --depth 1 --branch "v0.36.0" https://github.com/nextlinux/gosbom

FROM docker.io/nextlinux/govulners:v0.32.0 as govulners-binary
FROM docker.io/nextlinux/gosbom:v0.36.0 as gosbom-binary
FROM scratch

COPY --from=go-src /go/src/govulners/go.mod /go/src/govulners/
COPY --from=go-src /go/src/gosbom/go.mod /go/src/gosbom/

COPY --from=govulners-binary /govulners /usr/local/bin/
COPY --from=gosbom-binary /gosbom /usr/local/bin/
