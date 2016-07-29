# Docker

## Containers

With containers, the host kernel is shared, therefore the containers must use
the same kernel version (and type - so it is not possible to run a 'Windows'
container on Linux).

## Shutdown process

Containers only run as long as their main process. However, exiting the main
process will only stop the container, it will not remove it from disk. To do
this you must run: `docker rm [container]`.

`docker ps -a` will show all containers, included those which have been stopped.

Passing `--rm` to `docker run` will automatically delete the container when the
main process exits, e.g.

```
docker run --rm debian echo "Hello World"
```

All Docker containers can be removed with the following command:

```
docker rm -v $(docker ps -aq -f status=exited)
```

## Dockerfile

Docker configuration is contained in a file called `Dockerfile`.

The first non-comment line of a Dockerfile must be `FROM`, followed by the name
of the base image. For example:

```
FROM debian:jessie
```

The container can then be built using:

```
docker build .
```

Each line in the Dockerfile is a *layer*, implemented as a read-only filesystem
on top of the image. Due to the cost of large numbers of layers, and the fact
that some filesystems (e.g. AUFS) have a hard limit, you may see many commands
combined into a single RUN instruction.
