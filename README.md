# docker-concepts-commands
Just a handy reference for various docker related concepts and commands







# Concepts
    ## Container
      Docker is an engine that runs containers
      Host can run multiple containers isolated with each other
      The Docker daemon - **dockerd** listens for Docker API requests and manages host's Container life-cycles by utilizing **contanerd** (executor for containers)
    ## Image
      Many container can be created from a single image
    ## Image Layers
      Image are made of multiple layers.
      Each layer except, the very last one, is read-only.
      Docker caches layers when pulling and pushing images
    ## Registry
      Holds images
     .dockerignore - used to skip files being copied
    ## Multistage Dockerfiles
       COPY --from=image1 /preppedirectory .


# Commands

    docker run hello-world
    docker container run –it busybox
    docker run -d alpine ping www.docker.com
    docker run --rm -it -p 8085:80 learnbook/webserver
    docker container run -p [HOST_PORT]:[CONTAINER_PORT]/tcp -p [HOST_PORT]:[CONTAINER_PORT]/udp [IMAGE]
    docker ps <container-ID>
    docker inspect <container-ID>
    docker logs <container-ID>
    docker stop <container-ID>
    docker rm <container-ID>
    docker container prune -f

    docker image prune -f
    docker image prune --all
    docker images ls
    docker run -d -p 8085(External):80(Internal) nginx
    (volumes)
    docker run -v /your/dir:/var/lib/mysql -d mysql:10.5
    docker volume create test-volume1
    docker volume prune -f
    docker volume inspect test-volume1
    docker volume rm test-volume
    publish to registry using this format - <repository_name>/<name>:<tag>
    docker build -t hello . ( looks in Dockerfile locally)
    docker exec -i -t CONTAINER_ID /bin/bash
    docker rmi image_id
    docker run --rm -e host=www.bing.com pinger
    docker login ( to Registry)
    docker push ( to Registry)
    docker tag webserver mylearnbook/webserver
    docker push mylearnbook/webserver
    docker stats
    docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 br02
    docker network inspect br02
    docker network rm [NAME]
    docker network prune
    docker network connect br01 network-test03
    docker container run -d --name network-test02 --ip 10.1.4.102 --network br04 nginx
    docker container run --name network-test01 -it --network br04 centos /bin/bash


# Dockerfile commands
    Reference - https://docs.docker.com/engine/reference/builder/
    FROM debian:8
    CMD ["echo", "Hello world"]
    COPY index.html /usr/share/nginx/html
    ENV host=www.google.com
    EXPOSE 80
    ENTRYPOINT instruction makes sure that the code has started inside the container.
    ENTRYPOINT allows us to configure a container that will run as an executable.
    We can override all elements specified using CMD.
    Using the docker run --entrypoint flag will override the ENTRYPOINT instruction.


# Restart modes
    --restart always
    --restart unless-stopped

# docker image:

    build Build an image from a dockerfile
    history Show the history of an image
    import Import the contents from a tarball to create a filesystem image
    inspect Display detailed information on one or more images
    load Load an image from a tar file or STDIN
    ls List images
    prune Remove unused images
    pull Pull an image or a repository from a registry
    push Push an image or a repository to a registry
    rm Remove one or more images
    save Save one or more images to a tar file (streamed to STDOUT by default)
    tag Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE

# docker container:

    attach Attach local standard input, output, and error streams to a running container
    commit Create a new image from a container's changes
    cp Copy files/folders between a container and the local filesystem
    create Create a new container
    diff Inspect changes to files or directories on a container's filesystem
    exec Run a command in a running container
    export Export a container's filesystem as a tar archive
    inspect Display detailed information on one or more containers
    kill Kill one or more running containers
    logs Fetch the logs of a container
    ls List containers
    pause Pause all processes within one or more containers
    port List port mappings or a specific mapping for the container
    prune Remove all stopped containers
    rename Rename a container
    restart Restart one or more containers
    rm Remove one or more containers
    run Run a command in a new container
    start Start one or more stopped containers
    stats Display a live stream of container(s) resource usage statistics
    stop Stop one or more running containers
    top Display the running processes of a container
    unpause Unpause all processes within one or more containers
    update Update configuration of one or more containers
    wait Block until one or more containers stop, then print their exit codes

# Network Drivers:

    bridge
    host
    overlay
    macvlan
    none
    Network plugins

# Docker security
    Namespaces provide isolation.
    Control Groups are about setting limits for: CPU, RAM and Disk I/O

# Docker compose commands
    https://docs.docker.com/compose/compose-file/
    build: Build or rebuild services
    bundle: Generate a Docker bundle from the Compose file
    config: Validate and view the Compose file
    create: Create services
    down: Stop and remove containers, networks, images, and volumes
    events: Receive real time events from containers
    exec: Execute a command in a running container
    help: Get help on a command
    images: List images
    kill: Kill containers
    logs: View output from containers
    pause: Pause services
    port: Print the public port for a port binding
    ps: List containers
    pull: Pull service images
    push: Push service images
    restart: Restart services
    rm: Remove stopped containers
    run: Run a one-off command
    scale: Set number of containers for a service
    start: Start services
    stop: Stop services
    top: Display the running processes
    unpause: Unpause services
    up: Create and start containers
    version: Show the Docker-Compose version information
