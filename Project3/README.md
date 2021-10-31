# Project 2 Documentation

## Container engine 1: Docker

### Available mount type(S) - Docker
- Volumes
    - Create and manage volumes 
        - `docker volume create volume_name` to create volume
        - `docker volume ls` to list volumes
        - `docker volume inspect volume_name` to check volume physical location
        - `docker volume rm volume_name` to remove a volume 
    - Start a container with a volume
        - If start a container with a volume that does'nt exist, Docker will create it.
        - Example: mount the volume `myvol` into /app/ in the container.
        - ` docker run -d \`
          `--name demo_one \`
          `--mount source=myvol,target=/app \`
          `busybox`
        - source: the name of the volume
        - target — location in container filesystem where the volume should be mounted
- Reference Link: https://docs.docker.com/storage/volumes/

- Bind Mounts
    - Start a container with a bind mount
        - `docker run -d \`
          `-it \`
          `--name demo_two \`
          ` --mount type=bind,source="$(pwd)"/target,target=/app \`
          `busybox`
        - type: the type of the mount
        - source: the path to the file or directory on the Docker daemon host.
        - destination: takes as its value the path where the file or directory is mounted in the container.
    - `docker inspect container_name` to vertify the bind mount was created correctly
- Reference Link: https://docs.docker.com/storage/bind-mounts/

- tmpfs mounts
    - If you running Docker on Linux, there is a third option: tmpfs mounts. 
    - When you create a container with a tmpfs mount, the container can create files outside the container’s writable layer.
    - tmpfs mount is temporary
    - can’t share tmpfs mounts between containers
    - Use a tmpfs mount in a container, Example: 
        - `docker run -d \`
          `-it \`
          `--name demo_three \`
          `--mount type=tmpfs,destination=/app \`
          `busybox`
- Reference Link: https://docs.docker.com/storage/tmpfs/

###  Building Images - Docker
- Build a image from a Dockerfile
    - `mkdir my_build` to create a working directory and place Dockerfile there
    - `touch Dockerfile` to create a Dockerfile
    - `vim Dockerfile` to start edit the content to the Dockerfile
    - Syntax of a Dockerfile
        - `# Comment` : Docker treats lines that begin with # as a comment,
        - `FROM` :must be the first instruction in the Dockerfile.
        - `FROM <image>` : Specifies the Parent Image from which you are building
        - `FROM <image>:<tag>` :use a specific version of base image
        - `MAINTAINER <name>`: allows you to set the Author field of the generated images
        - `CMD` : only one CMD instruction in a Dockerfile, provide defaults for an executing container
        - `RUN <command>` : the command is run in a shell
        - `EXPOSE <port> [<port>/<protocol>...]` :  informs Docker that the container listens on the specified network ports at runtime.
        - `ADD [--chown=<user>:<group>] <src>... <dest>` : copies new files, directories or remote file URLs from <src> and adds them to the filesystem of the image at the path <dest>.
        - ` COPY [--chown=<user>:<group>] <src>... <dest>` :  copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.
    - `docker build -t image_name:1.0` to build a image from a Dockerfile 
    - `docker images` to check the build image
- Reference Link: https://docs.docker.com/engine/reference/builder/


## Container engine 2: Podman

### Available mount type(S) - Podman
- Podman-mount
    - `podman mount [options] [container_id …]` 
    - Mounts the specified containers’ root file system in a location which can be accessed from the host, and returns its location.
    - options
        - `--all, -a` : Mount all containers
        - `--format` : Print the mounted containers in specified format
        - `--latest, -l` : use the latest created container
        - `--notruncate` : Do not truncate IDs in output
- Reference Link: https://manpages.ubuntu.com/manpages/groovy/man1/podman-mount.1.html

###  Building Images - Podman
- Podman commands are the same as Docker’s
- Syntax of a Dockerfile
    - `# Comment` : Docker treats lines that begin with # as a comment,
    - `FROM` :must be the first instruction in the Dockerfile.
    - `FROM <image>` : Specifies the Parent Image from which you are building
    - `FROM <image>:<tag>` :use a specific version of base image
    - `MAINTAINER <name>`: allows you to set the Author field of the generated images
    - `CMD` : only one CMD instruction in a Dockerfile, provide defaults for an executing container
    - `RUN <command>` : the command is run in a shell
    - `EXPOSE <port> [<port>/<protocol>...]` :  informs Docker that the container listens on the specified network ports at runtime.
    - `ADD [--chown=<user>:<group>] <src>... <dest>` : copies new files, directories or remote file URLs from <src> and adds them to the filesystem of the image at the path <dest>.
    - ` COPY [--chown=<user>:<group>] <src>... <dest>` :  copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.
- `podman build -t image_name:1.0` to build a image from a Dockerfile 
- `podman images` to check the build image
