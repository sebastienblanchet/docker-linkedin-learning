# Notes

- [Notes](#notes)
  - [Chapter 3: Building Docker Files](#chapter-3-building-docker-files)
    - [3.1 Intro](#31-intro)
    - [3.2 Building](#32-building)

## Chapter 3: Building Docker Files

### 3.1 Intro

> What ? Small program to create image

```bash
docker build -t {name} .

# dockerfiles uses cached
# NOT shell scripts
# each line is a container, passed into next etc..

## persistent environment vars
ENV {name}
```

### 3.2 Building

```bash
docker build -t first .
Sending build context to Docker daemon  3.072kB
Step 1/3 : FROM debian:sid
sid: Pulling from library/debian
e4396830990b: Pull complete
Digest: sha256:44fddf620226afb17de9a31704fed92360aa42f91c9f6d25ae3b81baae8552f0
Status: Downloaded newer image for debian:sid
 ---> 3d8c54e4d4f3
Step 2/3 : RUN echo "building simple docker image"
 ---> Running in eef3c6d2b8ea
building simple docker image
Removing intermediate container eef3c6d2b8ea
 ---> 2cd85d096576
Step 3/3 : CMD echo "first container from dockerfile"
 ---> Running in efcb287835d2
Removing intermediate container efcb287835d2
 ---> 1accfc4d4da1
Successfully built 1accfc4d4da1
Successfully tagged first:latest
```