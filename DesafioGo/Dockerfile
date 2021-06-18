FROM golang@sha256:0991060a1447cf648bab7f6bb60335d1243930e38420bee8fec3db1267b84cfa as builder
RUN apk update && apk add --no-cache git
WORKDIR $GOPATH/src/fullcycle/hello/
COPY . .
RUN go get -d -v
# -ldflags "-w" remove opções de debug (reduz tamanho executavel)
RUN go build -o /go/bin/hello -ldflags "-w"
FROM scratch
COPY --from=builder /go/bin/hello /go/bin/hello
CMD ["/go/bin/hello"]
