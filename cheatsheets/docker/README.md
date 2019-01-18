
# Docker Commands

list images

```bash
docker image ls
```

list all containers including not runnings

```bash
docker ps -a
```

delete image

```bash
docker rmi <image>
```

delete container

```bash
docker rm <container>
```

pull image from repo

```bash
docker pull <image>
```

run image

```bash
docker run <image>
```

run detached

```bash
docker run -d <image>
```

run image but delete container when it stops

```bash
docker run --rm <image>
```

start|stop container

```bash
docker start|stop <container>
```

show logs of the container

```bash
docker logs -f <container>
```

connect to container and open bash console

```bash
docker exec -it <container> /bin/bash
```

tag an image for remote repository

```bash
docker tag <repository>/<image>:<tag> <registry_address>:<registry_port>/<repository>/<image>:<tag>
```

push an image to repository

```bash
docker push <registry_address>:<registry_port>/<repository>/<image>:<tag>
```

Inspect container and get ip address info

```bash
docker inspect <container id> | grep "IPAddress"
```

Inspect container and mounted volumes

```bash
docker inspect -f '{{ .Mounts }}' <container>
```

## Docker Compose Commands

```bash
docker compose build --no-cache
```

```bash
docker compose up -d
```

```bash
docker compose stop
```

```bash
docker compose down
```

```bash
docker-compose rm -f
```

## Dangerous Commands

stop all containers

```bash
docker stop $(docker ps -a -q)
```

delete all containers

```bash
docker rm $(docker ps -a -q)
```

delete dangling images

```bash
docker rmi $(docker images -f "dangling=true" -q)
```
