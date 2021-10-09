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
- Reference Link: 
[Docker]https://docs.docker.com/engine/install/ubuntu/
 
## Pulling a container image: busybox
- `docker pull busybox`
- How to view container images on the system
    - `docker images`

## Running a container 
- Define the modes below and why you would want to pick each
- Initializing versus running the container, and why there is a difference
- Run and enter shell
    - `docker run -it busybox`
- Run in detached mode
    - `docker -d busybox`

## Logs & Status
- Finding out the status of the container
    - `docker ps` - running containers only
    - `docker top [container_id]`
    - `docker ps -a` - all container 
- Reading the logs of a running container
    - `docker logs <container_id>`

## Stopping a container
- Pause
    - `docker pause [container_id]`
- Restart / Resume
- Stop / Kill
    - `docker stop [container_id]`
    - `Kill PID`
- Remove
    - `docker rm [container_id]`

## Container engine 2:

## Installation instructions
- LXC is available on Ubuntu default repositories
- Use `sudo apt-get install lxc lxctl lxc-templates` command to install it and its derivatives.
- Use `sudo lxc-checkconfig` to check everything is OK

## Pulling a container image:
- Pick a base image to tinker with. Write instructions for pulling each with each
- How to view container images on the system

## Running a container
- Define the modes below and why you would want to pick each
- Initializing versus running the container, and why there is a difference
- Run and enter shell
- Run in detached mode

## Logs & Status
- Finding out the status of the container
- Reading the logs of a running container

## Stopping a container
- Pause
- Restart / Resume
- Stop / Kill

 
https://linuxcontainers.org/lxc/getting-started/
https://www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/