FROM golang:1.12.4-stretch
ENV GO111MODULE=on
WORKDIR /module
COPY . /module/
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 \
  go build -a -tags netgo \
    -ldflags '-w -extldflags "-static"' \
    -o foo
 
FROM scratch
COPY --from=0 /module/foo .
ENTRYPOINT ["/foo"]
