# Notes

- [Notes](#notes)
  - [Chapter 4: Under the Hood](#chapter-4-under-the-hood)
    - [4.1 Docker Program](#41-docker-program)
    - [4.2 Network & Namespaces](#42-network--namespaces)

## Chapter 4: Under the Hood

### 4.1 Docker Program

* Uses `cgroups` to contain processes
* Uses `namespaces` to contain networks
* Uses `copy-on-write` filesystems to build images
* Docker is 2 programs: client & server

**Scripting distributed systems**

Found in `/var/run/docker.sock`.

### 4.2 Network & Namespaces