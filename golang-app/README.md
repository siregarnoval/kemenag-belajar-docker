# Create First Docker Image Golang

## Create Dockerfile

```Dockerfile
FROM golang:1.22.1

WORKDIR /go/src/app

COPY . .
RUN go mod download
RUN go build -o /go/bin/app/main cmd/main.go

EXPORT 3000

ENTRYPOINT ["/go/bin/app/main"]
```

## Build Docker Image

```bash
docker build -t golang-app:latest .
```

## Running First Docker Container

```bash
docker run -it \
--rm \
-d \
-p 3000:3000 \
--volume "./.env:/go/src/app/.env" \
--name golang-app-1 \
golang-app:latest
```

## Check Docker Container

```bash
docker ps
```

## Check Docker Container Logs

```bash
docker logs golang-app-1
```

## Access Docker Container

```bash
curl http://localhost:3000/person
```
