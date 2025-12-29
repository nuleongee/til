# Docker tutorial

## Dockerfile

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
```

### docker build

```shell
docker build -t <image_name> .
```

### docker multi-arch build

```shell
docker buildx build --platform linux/amd64,linux/arm64 -t <image_name> .
docker buildx build --platform linux/amd64,linux/arm64 -t <repo>/<name>:<tag> --push .
```

### docker run

```shell
docker run -dp 3000:3000 <image_name>
```

## Update

### docker ps

```shell
docker ps
```

### docker stop

```shell
docker stop <container_id>
```

### docker rm

```shell
docker rm <container_id>
```

### docker rm -f

```shell
docker rm -f <container_id>
```

## Share

### docker login

```shell
docker login -u <username>
```

### docker tag

```shell
docker tag <image_name> <username>/<image_name>
```

### docker push

```shell
docker push <username>/<image_name>
```
