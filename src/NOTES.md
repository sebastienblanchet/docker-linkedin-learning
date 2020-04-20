# Notes

- [Notes](#notes)
  - [Chapter 2: Using Docker](#chapter-2-using-docker)
    - [2.1 Images to Containers](#21-images-to-containers)
    - [2.2 Containers to Images](#22-containers-to-images)
    - [2.3 Running Things in Docker](#23-running-things-in-docker)
      - [2.4 Manage Containers](#24-manage-containers)
      - [2.5 Exposing Port](#25-exposing-port)
      - [2.6 Container Networking](#26-container-networking)
      - [2.8 Images](#28-images)
      - [2.9 Volumes](#29-volumes)
      - [2.10 Registries](#210-registries)

## Chapter 2: Using Docker

### 2.1 Images to Containers

Containers from images:

```bash
# list images
docker images

# Run shell within image
docker run -ti {name}
# i.e. image to container
docker run {name}

# see running container
docker ps
```

### 2.2 Containers to Images

```bash
# create new container
docker run -ti ubuntu bash

# enter and exit

# list exited containers
docker ps -l

# get the container id of interest
# containers 2 images
docker commit {containerId}

## get the sha256 that ^^ returns and tag
docker tag {sha256Id} {newName}

# OR
docker commit {containerName} {newName}
```

### 2.3 Running Things in Docker

Containers are processes

```bash
# don't keep container afterwards
docker run --rm --it {os} {cmd}
docker run --rm --it {os} bash -c "{bashScript}"

# detached containers, will return command id
docker run -d --ti ubuntu bash

# start detached and re enter it
docker attach {name}

# can do this within container CTRL+P CTRL+Q

# re enter an existing container
docker exec -ti {containerName}
```

#### 2.4 Manage Containers

```bash
# logs
docker logs {containerName}

# kill or rm container
docker kill {containerName}
docker rm {containerName}

# dont let container fetch depts
# dont leave important things unnamed
```

#### 2.5 Exposing Port

```bash
# exposing ports
docker run --rm --ti -p {outsidePort}:{internalPort} --name {name} {os} bash

# example program i.e. loopback
nc -lp {port1} | nc -lp {port2}

# NAME USED FOR DOCKER TO REFER PC THAT IS HOSTING CONTAINER
host.docker.internal

# exposing dynamic ports
docker port {containerName}

# specifying type
docker run -p {outsidePort}:{internalPort}/{protocol: tcp|udp}
```

#### 2.6 Container Networking

```bash
# list container networks
docker network ls

# create a named network
docker run --rm -ti --net {netName} --name {actualName}

# same
docker network create {name}
```

#### 2.8 Images

```bash
# list from local machine
docker images

# automatically run by docker run
docker pull

# remove images
docker rmi
```

#### 2.9 Volumes

```bash
# virtual discs either persistent or ephemeral
# not part of images

# shared folders i.e. with host & docker
docker run -ti -v {pathToHostSharedFolder} ubuntu bash

# can also do this with a single file, just pass in fpath

# sharing within containers
# volumes from
docker run -ti -v {dockerPathToShared} ubuntu bash
# get name ^^
docker run -ti --volumes-from {containerName}

# volumes are ephemeral
```

#### 2.10 Registries

```bash
#registries manage & dist imgs

# search
docker search {imageToSearch}

# log into machine to share token
docker login
docker pull {imgToDownload}
```
