See [Docker official documentation](https://docs.docker.com/) for details.
See [Fig official documentation](http://www.fig.sh/) for details.

docker - remove unused images
-----------------------------

```
docker rmi -f $(docker images --filter "dangling=true" -q --no-trunc)
```

docker - remove all containers
------------------------------

```
docker rm -f $(docker ps -a -q)
```

docker - list images
--------------------

```shell
docker images
```

docker - rm image
-----------------

```shell
docker rmi -f [image-id]
```

docker - list containers
------------------------

```shell
docker ps
```

docker - logs
-------------

```shell
docker logs [OPTIONS] CONTAINER
```

docker - rm container
---------------------

```shell
docker rm -f [container-id]
```

docker - execute a command 
--------------------------

```shell
docker exec -i -t [container-id] bash
```

fig - remove containers
-----------------------

```shell
fig rm --force
```




