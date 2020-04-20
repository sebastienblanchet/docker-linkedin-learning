# Notes

- [Notes](#notes)
  - [Chapter 4: Under the Hood](#chapter-4-under-the-hood)
    - [4.1 Docker Program](#41-docker-program)
    - [4.2 Network & Namespaces](#42-network--namespaces)
    - [4.3 Processes & cgroups](#43-processes--cgroups)
    - [4.4 Storage](#44-storage)

## Chapter 4: Under the Hood

### 4.1 Docker Program

* Uses `cgroups` to contain processes
* Uses `namespaces` to contain networks
* Uses `copy-on-write` filesystems to build images
* Docker is 2 programs: client & server

**Scripting distributed systems**

Found in `/var/run/docker.sock`.

### 4.2 Network & Namespaces

> uses bridges (i.e. software switches) to create virtual network

Within docker, download and run:
```
brctl show

# outside
docker network create {name}

# will now have ^^
brctl show

# show how docker uses port forwarding to RX/TX packets
# network adressing tabes
sudo iptables -n -L -t nat

# run docker with all accesses to local network
docker run -ti --rm --net=host --privileged=true ubuntu bash

# REALLY JUST PORT FORWARDING
docker run -p 8080:8080
```

### 4.3 Processes & cgroups

> Docker starts with init (usual), when init exits, container is dead

```bash
## starting a container and finding init PID
docker run -ti --rm --name {name} ubuntu bash
#jQuery like
docker inspect --format '{{.State.Pid}}' {name}

# adding --pid=host to docker run allow access to kill proccess

# ressource limiting
```

### 4.4 Storage

Docker is really just:
* actual store (ssd)
  * paritions of that drives
    * filesystems
      * programs as filesystem (COWS: copy on write system)

> COWS: start with base ref and ANY write ops is actually just a **copy**

```bash
# recall the DWTFYW container
docker run -ti --rm --priviliged=true ubuntu bash

# make some files in multiple dirs
ls -R

# MOUNT Order is important
mount -o bind dir1 dir2
# files from dir2 will be UNDER the contents from dir1

#revert
umount dir2
```