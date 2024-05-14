# Kemenag Belajar Docker

## Pull Docker Image

```
docker pull nginx:latest
```

```
docker pull nginx:alpine
```

## Running First Docker Container

```
docker run -it --rm -d -p 8080:80 --name web-server-1 nginx:latest
```

```
docker run -it --rm -d -p 8081:80 --name web-server-2 nginx:alpine
```

## Check Docker Container

```
docker ps
```

## Check Docker Container Logs

```
docker logs web-server-1
```

```
docker logs web-server-2
```

## Access Docker Container

```
curl http://localhost:8080
```

```
curl http://localhost:8081
```

## Check Usage of Docker Container

```
docker stats web-server-1
```

```
docker stats web-server-2
```

## Stop Docker Container

```
docker stop web-server-1
```

```
docker stop web-server-2
```

## Remove Docker Container

```
docker rm web-server-1
```

```
docker rm web-server-2
```

## Remove Docker Image

```
docker rmi nginx:latest
```

```
docker rmi nginx:alpine
```
