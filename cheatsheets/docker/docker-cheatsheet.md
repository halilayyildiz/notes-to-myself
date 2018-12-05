Docker Commands
--------------------------------

docker images
docker image ls
docker container ls -a
docker ps -a

> docker rmi
> docker rm

> docker pull <image>

Run images
> docker run <image>

run image but delete container when it stops
> docker run --rm <image>


```docker start|stop <container>```

```docker logs -f <container>```

Connect to container and open bash console
```docker exec -it <container> /bin/bash```

docker run -d -p 5000:5000 --restart=always --name registry registry:2

docker tag noms/topo-tracer:latest 35.156.234.183:5000/noms/topo-tracer:0.0.1
docker push 35.156.234.183:5000/noms/topo-tracer:0.0.1
docker tag noms/outage-management:latest 35.156.234.183:5000/noms/outage-management:0.0.1
docker push 35.156.234.183:5000/noms/outage-management:0.0.1


docker compose up -d
docker compose stop
docker compose down
docker-compose rm -f
docker compose build --no-cache

docker inspect <container id> | grep "IPAddress"
docker inspect -f '{{ .Mounts }}' <container>

docker commit <container> (name/product:version)
docker save <container> target_name.tar
docker load

docker-machine start|stop|restart
docker-machine ip defult



!!!!!!!! dangerous !!!!!!!!!!!!!!!!!!!!!!

docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)

docker rmi $(docker images -f "dangling=true" -q)

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


Install GitLab Runner
Specify the following URL during the Runner setup:https://code.siemens.com/ 
Use the following registration token during setup:jFWQFsp6dY9KQ1TxBYj8 
Start the Runner!

https://code.siemens.com/
jFWQFsp6dY9KQ1TxBYj8
siguard-runner-docker
docker,maven

curl -v https://code.siemens.com/ci/api/v1/runners/register.json

docker exec -it gitlab-runner gitlab-runner register \
  --non-interactive \
  --url "https://code.siemens.com/" \
  --registration-token "jFWQFsp6dY9KQ1TxBYj8" \
  --executor "docker" \
  --description "docker-runner" \
  --tag-list "docker,maven" \
  --run-untagged \
  --locked="false"