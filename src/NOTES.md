# Notes

- [Notes](#notes)
  - [Chapter 5: Orchestration Build Systems with Docker](#chapter-5-orchestration-build-systems-with-docker)
    - [5.1 Registries](#51-registries)

## Chapter 5: Orchestration Build Systems with Docker

### 5.1 Registries

```bash
docker run -d -p 5000:5000 --restart=always --name reg reg:2

# tag and push to local registry
docker tag ubuntu localhost:5000/myorg/mylinux:99
docker push localhost:5000/myorg/mylinux:99

# OR
docker save -o fName.tar.gz {img1, img2, ...}
docker rmi {img1, img2, ...}
docker load -i fName.tar.gz
```