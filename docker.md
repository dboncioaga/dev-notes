# **Docker Cheat Sheet**

---

## **DOCKER BASICS**
### Check Installed Docker Version
```bash
docker --version
docker info              #Display system-wide information about Docker
```
### Help
```bash
docker help             # General help
docker <command> --help # Help for a specific command
```

## Containers
### List Containers
```bash
docker ps                        # List running containers
docker ps -a                     # List all containers (running + stopped)
docker ps -q                     # List container IDs only
docker ps --filter status=exited # List stopped containers
```

### Run Containers
```bash
docker run <image>               # Run a container in the foreground
docker run -d <image>            # Run a container in the background (detached)
docker run --name <name> <image> # Assign a name to the container
docker run -p 8080:80 <image>    # Map container port 80 to host port 8080
docker run -v /host/path:/container/path <image> # Mount a volume
docker run -it <image> /bin/bash # Run interactively (great for debugging)
```

### Start Stop Containers
```bash
docker start <container_id_or_name>   # Start a stopped container
docker stop <container_id_or_name>    # Stop a running container
docker restart <container_id_or_name> # Restart a container
```

### Remove Containers
```bash
docker rm <container_id_or_name>   # Remove a specific container
docker container prune             # Remove all stopped containers
```

### View Containers
```bash
docker logs <container_id_or_name>                  # View logs for a container
docker logs -f <container_id_or_name>              # Follow logs in real time
docker logs --since 10m <container_id_or_name>     # Show logs from the last 10 minutes
```

### Access Containers
```bash
docker exec -it <container_id_or_name> bash        # Run a shell in the running container
docker attach <container_id_or_name>              # Attach to a running container’s stdin
```

### Continers Resource Limits
```bash
docker run --memory="256m" --cpu-shares=512 <image> # Set memory and CPU limits
```

## Images

```bash
docker images                           # List all local images
docker image ls                         # Same as above

docker pull <image_name>                # Pull an image from Docker Hub or custom registry
docker pull <image_name>:<tag>          # Pull a specific tag (e.g., `nginx:latest`)

docker rmi <image_id_or_name>           # Remove a specific image
docker image prune                      # Remove unused images
docker image prune -a                   # Remove all unused images and dangling layers

docker tag <image_id> <new_name>:<tag> # Tag an image for pushing or referencing locally
docker push <image>:<tag>              # Push an image to a Docker registry

```


## Volumes
```bash
docker volume ls              # List all volumes
docker volume create <name>   # Create a named volume
docker volume rm <name>       # Remove a specific volume
docker volume prune           # Remove all unused volumes
docker run -v <volume_name>:/path/in/container <image>
```

## Networking
```bash
docker network ls                                   # List all networks
docker network create <network_name>                # Create a user-defined bridge network
docker network connect <network_name> <container>   # Connect a container to a network
docker network disconnect <network_name> <container> #Disconnect a container from a network
docker network rm <network_name>                    # Remove a custom network
docker network prune                                # Remove all unused networks

```

## Docker Compose
```bash
docker-compose up                   # Build, (re)create, start, and attach containers
docker-compose up -d                # Run containers in the background (detached)
docker-compose down                 # Stop and remove services defined in the compose file

docker-compose build                # Build or rebuild services
docker-compose build --no-cache     # Build without using cache

docker-compose up --scale <service>=<number> # Scale services to multiple containers

docker-compose logs
docker-compose logs -f                # Follow logs in real time
```

## Cleanup 
```bash
docker system prune                   # Remove unused data (containers, networks, images)
docker system prune -a                # Include unused images as well

docker container rm $(docker ps -aq) # Remove all containers
docker rmi $(docker images -q)       # Remove all images
docker volume rm $(docker volume ls -q) # Remove all volumes
```

## Monitoring and Inspection
```bash
docker inspect <container_id_or_name>   # Detailed configuration info about a container
docker inspect <image_id_or_name>       # Detailed configuration info about an image
docker stats                            # Show resource usage for running containers
docker stats <container_id_or_name>     # Show resource usage for a specific container
```

## Backup and Restore
```bash
docker save -o <file>.tar <image>       # Save image to a file
docker load -i <file>.tar               # Load image from a file

docker export <container_id> > <file>.tar # Export a running/stopped container to a file
docker import < <file>.tar               # Import a container from an exported file
```

## Debugging
```bash
docker logs <container>                 # View logs
docker exec -it <container> bash        # Connect to the container interactively
docker inspect <container>              # Get detailed info about the container

docker network inspect <network_name>   # Inspect network configuration
docker logs <container>                 # Check logs for network issues
```
