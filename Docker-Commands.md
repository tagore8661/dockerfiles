# Docker Commands Cheat Sheet

This file contains all major Docker commands, grouped by category, with simple explanations for each.

---

## 1. Docker Basics

- `docker --version`  
  Show Docker version installed.
- `docker version`  
  Show Docker client and server version info.
- `docker info`  
  Display system-wide Docker information.
- `docker help`  
  List all Docker commands and options.
- `docker login -u <username> -p <password>`  
  Log in to a Docker registry with username and password.
- `docker logout`  
  Log out from a Docker registry.
- `docker context ls`  
  List available Docker contexts.
- `docker context use <context>`  
  Switch to a different Docker context (useful for remote Docker hosts).

---

## 2. Images

- `docker images`  
  List all local Docker images.
- `docker pull <image>`  
  Download an image from Docker Hub or other registry.
- `docker build -t <name> .`  
  Build an image from a Dockerfile in the current directory and tag it.
- `docker rmi <image>`  
  Remove an image from local storage.
- `docker tag <image> <newname>`  
  Tag an image with a new name (useful for pushing to a registry).
- `docker push <image>`  
  Upload an image to Docker Hub or another registry.
- `docker image inspect <image>`  
  View detailed information about an image.
- `docker image history <image>`  
  Show history of changes for an image.
- `docker history <image>`  
  Show history of an image.
- `docker image prune`  
  Remove unused images.
- `docker image ls --filter dangling=true`  
  List dangling (untagged) images.
- `docker search <image>`  
  Search Docker Hub for images.

---

## 3. Containers

- `docker create <image>`  
  Create a new container from an image (does not start it).
- `docker run <image>`  
  Create and start a container from an image. Most common way to launch containers.
- `docker run -d <image>`  
  Run a container in detached (background) mode.
- `docker run -it <image> /bin/bash`  
  Run a container interactively with a shell (useful for debugging or manual setup).
- `docker run -p <host_port>:<container_port> <image>`  
  Map a port from the host to the container (e.g., `-p 8080:80` exposes container's port 80 on host's port 8080).
- `docker run -e <VAR>=<value> <image>`  
  Set environment variables in the container.
- `docker run --name <container_name> <image>`  
  Assign a custom name to the container.
- `docker run --restart=always <image>`  
  Automatically restart the container if it stops or Docker restarts.
- `docker run --rm <image>`  
  Remove the container automatically when it exits.
- `docker run --memory="512m" --cpus="1.0" <image>`  
  Limit container memory and CPU usage.
- `docker run -v <volume>:/path <image>`  
  Mount a volume in a container for persistent storage.
- `docker run --network <name> <image>`  
  Connect a container to a specific network.
- `docker run --detach --publish <host_port>:<container_port> --env <VAR>=<value> --name <container_name> <image>`  
  Example of combining multiple options for a production container.
- `docker run --entrypoint <executable> <image>`  
  Override the default entrypoint of the image.
- `docker run --user <username|uid>`  
  Run container as a specific user.
- `docker run --workdir <dir>`  
  Set working directory inside the container.
- `docker run --label <key>=<value>`  
  Add metadata label to container.
- `docker ps`  
  List running containers.
- `docker ps -a`  
  List all containers (including stopped).
- `docker start <container>`  
  Start a stopped container.
- `docker stop <container>`  
  Stop a running container.
- `docker restart <container>`  
  Restart a container.
- `docker pause <container>`  
  Pause all processes in a container.
- `docker unpause <container>`  
  Resume a paused container.
- `docker rm <container>`  
  Remove a container.
- `docker logs <container>`  
  View logs from a container.
- `docker exec -it <container> <command>`  
  Run a command inside a running container (e.g., open a shell or run a script).
- `docker top <container>`  
  Display running processes in a container.
- `docker inspect <container>`  
  Show detailed information about a container (configuration, network, mounts, etc.).
- `docker update <container> --restart=always`  
  Change restart policy for an existing container.
- `docker stats <container>`  
  Show live resource usage statistics for containers.
- `docker cp <container>:<src> <dest>`  
  Copy files/folders between container and host.
- `docker rename <container> <newname>`  
  Rename a container.
- `docker attach <container>`  
  Attach to a running container's output stream.
- `docker wait <container>`  
  Block until container stops, then print exit code.
- `docker kill <container>`  
  Send a SIGKILL to a running container.
- `docker commit <container> <new_image>`  
  Create a new image from a container's changes.
- `docker diff <container>`  
  Show changes to container filesystem since creation.

---

## 4. Volumes & Storage

- `docker volume create <name>`  
  Create a new volume for persistent data.
- `docker volume ls`  
  List all volumes.
- `docker volume inspect <name>`  
  Show details about a volume.
- `docker volume rm <name>`  
  Remove a volume.
- `docker run -v <volume>:/path <image>`  
  Mount a volume in a container for persistent storage.
- `docker volume prune`  
  Remove all unused volumes.
- `docker volume update <name> --label <key>=<value>`  
  Add or update volume labels.

---

## 5. Networks

- `docker network ls`  
  List all Docker networks.
- `docker network create <name>`  
  Create a new network.
- `docker network inspect <name>`  
  Show details about a network.
- `docker network rm <name>`  
  Remove a network.
- `docker run --network <name> <image>`  
  Connect a container to a network.
- `docker network prune`  
  Remove all unused networks.
- `docker network connect <network> <container>`  
  Connect a running container to a network.
- `docker network disconnect <network> <container>`  
  Disconnect a running container from a network.

---

## 6. Docker Compose

- `docker-compose up`  
  Start services defined in docker-compose.yml (use `-d` for detached mode).
- `docker-compose down`  
  Stop and remove services, networks, and volumes defined in Compose.
- `docker-compose ps`  
  List containers managed by Compose.
- `docker-compose logs`  
  View logs for Compose services.
- `docker-compose build`  
  Build images defined in Compose.
- `docker-compose exec <service> <command>`  
  Run a command in a running Compose service container.
- `docker-compose stop`  
  Stop services without removing them.
- `docker-compose restart`  
  Restart services.
- `docker-compose pull`  
  Pull service images defined in Compose.
- `docker-compose rm`  
  Remove stopped service containers.

---

## 7. System Cleanup

- `docker system prune`  
  Remove unused data (containers, images, volumes, networks) to free disk space.
- `docker image prune`  
  Remove unused images.
- `docker container prune`  
  Remove stopped containers.
- `docker volume prune`  
  Remove unused volumes.
- `docker network prune`  
  Remove unused networks.

---

## 8. Inspect & Troubleshoot

- `docker inspect <object>`  
  Return detailed information on images, containers, volumes, or networks.
- `docker stats`  
  Display resource usage statistics for containers.
- `docker events`  
  Get real-time events from the Docker server.
- `docker logs <container>`  
  View container logs for troubleshooting.
- `docker diff <container>`  
  Show changes to container filesystem since creation.
- `docker healthcheck`  
  Run a health check on a container (usually defined in Dockerfile).

---

## 9. Export & Import

- `docker save -o <file> <image>`  
  Save an image to a tar archive (for backup or transfer).
- `docker load -i <file>`  
  Load an image from a tar archive.
- `docker export <container> > <file>`  
  Export a container's filesystem to a tar archive (no history or layers).
- `docker import <file>`  
  Import a tar archive as an image.

---

## 10. Other Useful Commands

- `docker login`  
  Log in to a Docker registry.
- `docker logout`  
  Log out from a Docker registry.
- `docker history <image>`  
  Show history of an image.
- `docker update <container>`  
  Update container configuration (e.g., resource limits).
- `docker system df`  
  Show disk usage by Docker.
- `docker builder prune`  
  Remove build cache.

---

## 11. Security & Advanced

- `docker scan <image>`  
  Scan an image for vulnerabilities (requires Docker Desktop).
- `docker secret create <name> <file>`  
  Create a secret (Swarm mode).
- `docker secret ls`  
  List secrets (Swarm mode).
- `docker secret rm <name>`  
  Remove a secret (Swarm mode).
- `docker config create <name> <file>`  
  Create a config (Swarm mode).
- `docker config ls`  
  List configs (Swarm mode).
- `docker config rm <name>`  
  Remove a config (Swarm mode).
- `docker swarm init`  
  Initialize a Docker Swarm cluster.
- `docker swarm join`  
  Join a node to a Swarm cluster.
- `docker service create <options>`  
  Create a new service in Swarm mode.
- `docker service ls`  
  List services in Swarm mode.
- `docker service rm <service>`  
  Remove a service in Swarm mode.

---

> This cheat sheet covers all major and advanced Docker commands for daily use. Each command is grouped and explained for practical reference and learning.
