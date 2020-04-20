# Notes

- [Notes](#notes)
  - [Chapter 3: Building Docker Files](#chapter-3-building-docker-files)
    - [3.1 Intro](#31-intro)

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
