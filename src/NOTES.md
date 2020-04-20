# Notes

- [Notes](#notes)
  - [Chapter 3: Building Docker Files](#chapter-3-building-docker-files)
    - [3.1 Intro](#31-intro)
    - [3.2 Building](#32-building)
    - [3.3 Dockerfile Syntax](#33-dockerfile-syntax)

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
# ex output
docker build -t first .
Sending build context to Docker daemon  3.072kB
Step 1/3 : FROM debian:sid
Step 2/3 : RUN echo "building simple docker image"
Step 3/3 : CMD echo "first container from dockerfile"
```

### 3.3 Dockerfile Syntax

Keywords:

```dockerfile
FROM
MAINTAINER
RUN
ADD
ENV
ENTRYPOINT
CMD
EXPOSE
VOLUME
WORKDIR
USER
```
