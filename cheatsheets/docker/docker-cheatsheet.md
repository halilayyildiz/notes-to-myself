# Docker Commands
--------------------------------

list images
> docker images
> docker image ls

list all containers including not runnings
> docker ps -a
> docker container ls -a

delete image
> docker rmi

delete container
> docker rm

pull image from repo
> docker pull <image>

run image
> docker run <image>

run detached
> docker run -d <image>

run image but delete container when it stops
> docker run --rm <image>

start|stop container
> docker start|stop <container>

show logs 
> docker logs -f <container>

connect to container and open bash console
> docker exec -it <container> /bin/bash

> docker run -d -p 5000:5000 --restart=always --name registry registry:2

tag and push image to repository
> docker tag noms/topo-tracer:latest <repo_address>:<repo_port>/noms/topo-tracer:0.0.1
> docker push <repo_address>:<repo_port>/noms/topo-tracer:0.0.1

tag and push image to repository
> docker tag noms/outage-management:latest 35.156.234.183:5000/noms/outage-management:0.0.1
> docker push 35.156.234.183:5000/noms/outage-management:0.0.1


> docker compose up -d
> docker compose stop
> docker compose down
> docker-compose rm -f
> docker compose build --no-cache

> docker inspect <container id> | grep "IPAddress"
> docker inspect -f '{{ .Mounts }}' <container>

> docker commit <container> (name/product:version)
> docker save <container> target_name.tar
> docker load

> docker-machine start|stop|restart
> docker-machine ip defult



## Dangerous Commands

stop all containers
```
docker stop $(docker ps -a -q)
```

delete all containers
```
docker rm $(docker ps -a -q)
```

delete dangling images
```
docker rmi $(docker images -f "dangling=true" -q)
```

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

======================================================================


docker run -ti -p8080:8080 noms/outagemanagement:0.0.1


======================================================================




docker run -p 6379:6379 -d redis
docker run --rm --name redis-commander -d --env REDIS_HOSTS=192.168.99.100 -p 8081:8081 rediscommander/redis-commander:latest
docker run -d --hostname my-rabbit --name rabbitmq -p 15672:15672 rabbitmq:3-management
docker run --network=nomsnetwork -p 5432:5432 --name noms-postgres -e POSTGRES_PASSWORD=pass4admin -d postgres
docker run --network=nomsnetwork -p 80:80 	  --name noms-pgadmin -e "PGADMIN_DEFAULT_EMAIL=noms@siemens.com" -e "PGADMIN_DEFAULT_PASSWORD=pass4root" -d dpage/pgadmin4




docker run -d --name gitlab-runner --restart always \
  -v /srv/gitlab-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:ubuntu-v11.3.1


docker exec -it gitlab-runner gitlab-runner register
