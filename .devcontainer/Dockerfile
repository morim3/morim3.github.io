FROM golang:alpine as builder

RUN apk add --no-cache bash musl-dev gcc make g++ file docker-cli git tree

WORKDIR /temp
RUN git clone https://github.com/gohugoio/hugo.git
WORKDIR /temp/hugo
RUN GOBIN=/bin/ go install --tags extended


FROM golang:alpine
RUN apk add --no-cache bash git tree
RUN adduser devuser --disabled-password --gecos ""
COPY --from=builder /bin/hugo /bin/hugo

WORKDIR /workspace
USER devuser

