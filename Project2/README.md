# Project 2 Documentation

## Container engine 1: Docker

## Installation instructions - Install using the repository
- Set up the repository (so, I can install and update Docker from the repository.)
    - Update and upgrade the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:
        - `sudo apt-get update`
        -  `sudo apt-get install \`
            `apt-transport-https \`
            `ca-certificates \`
            ` curl \`
            ` gnupg \`
            `lsb-release`
    - Add Docker’s official GPG key:
        - ` curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
    - Set up the stable repository
        - `echo \`
        `"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/``docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \`
        `$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
- Install Docker Engine
    - Update the `apt`package index, and install the latest version of Docker Engine and containerd
        - `sudo apt-get update `
        - ` sudo apt-get install docker-ce docker-ce-cli containerd.io`
- Reference Link: https://docs.docker.com/engine/install/ubuntu/
 
## Pulling a container image: busybox
- `docker pull busybox`
- How to view container images on the system
    - `docker images`

## Running a container 
- Initializing vs. Running the container 
    - Initializing:
        - Docker App is a CLI plug-in that introduces a top-level docker app command to bring the container experience to applications
        - `docker app init` command is used to initialize a new Docker application project. If you run it on its own, it initializes a new empty project. If you point it to an existing docker-compose.yml file, it initializes a new project based on the Compose file.
    - Running
        - `docker run`, the container process that runs is isolated in that it has its own file system, networking, and isolated process tree separate from the host.
- Reference Link: https://docs.docker.com/engine/reference/commandline/app/
- Run and enter a interactive terminal
    - `docker run -it busybox`
- Run in detached mode ( in background)
    - `docker -d busybox`

## Logs & Status
- Finding out the status of the container
    - `docker ps` - running containers only
    - `docker top [container_id]` - display processes for a container
    - `docker ps -a` - all container 
- Reading the logs of a running container
    - `cat /var/lib/docker/containers/<container_id>/<container_id>-json.log`
    - `docker logs <container_id>`

## Stopping a container
- Pause
    - `docker pause [container_id]`
- Restart / Resume
    - `docker restart [container_id]`
- Stop / Kill
    - `docker stop [container_id]`
    - `Kill PID`
- Remove
    - `docker rm [container_id]`

## Container engine 2: LXC - Linux Container

## Installation instructions 
- In most cases, LXC available for Linux distribution
    - `sudo apt-get install lxc`
- LXD 
    - it is an open source container management extension for Linux Containers (LXC)
    - it improves existing LXC features and provides new features to build & manage LXC
    - Installation:
        - Install the snap package for the latest version
            - `sudo snap install lxd`

## Pulling a container image:
- Launch a new container of a particular release of an image
    - `lxc launch imageserver:imagename instancename`
    - for example: `lxc launch ubuntu:20.04 ubuntu`
        - `imageserver`: the name of a built-in or added image server
        - `imagename`: the name of an image
        - `instancename`: a name of your choice
- How to view container images on the system
    - `lxc image list images:` to list all images on server
    - `lxc list`: list all instances 

## Running a container
- Launch a new container of a particular release of an image
    - `lxc launch imageserver:imagename instancename`
- Run bash interactively in a container
    - `lxc exec instancename -- /bin/bash`

## Logs & Status
- List all containers (running and stopped)
    - `lxc info`
- Get detailed information about a particular container
    - `lxc info instancename`
    - for example: `lxc info ubuntu`

## Stopping a container
- pause an instance
    - `lxc pause instancename`
- stop an instance
    - `lxc stop instancename`
- remove an instance
    - `lxc delete instancename`
- Restart / Resume
    - `lxc restart instancename`
- Stop / Kill a running container
    - `lxc delete --force instancename`

## Reference Link
- https://linuxcontainers.org/lxc/getting-started/
- https://searchitoperations.techtarget.com/definition/LXD-Linux-container-hypervisor
- https://medium.com/@tcij1013/lxc-lxd-cheetsheet-effb5389922d