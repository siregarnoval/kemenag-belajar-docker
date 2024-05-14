FROM golang:1.22.1

WORKDIR /go/src/app

COPY . .
RUN go mod download
RUN go build -o /go/bin/app/main cmd/main.go

EXPOSE 3000

ENTRYPOINT ["/go/bin/app/main"]
