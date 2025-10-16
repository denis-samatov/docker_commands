# Docker Commands

Welcome to the **Docker Commands** repository! This project serves as a comprehensive, quick-reference guide to the most essential Docker commands.

The goal of this repository is to provide a clear and concise resource for developers of all skill levels—from beginners taking their first steps with Docker to experienced professionals who need a quick refresher on a specific command. Here, you will find a curated collection of commands for managing images, handling containers, debugging, and more, all supplemented with practical examples and explanations.

## Prerequisites

Before you begin, ensure you have Docker installed on your system. If you don't have it installed, you can download it from the official Docker website.

- [Install Docker](https://docs.docker.com/get-docker/)

## Table of Contents

1. [Building Images](#building-images)
2. [Dockerfile Basics](#dockerfile-basics)
3. [Managing Containers](#managing-containers)
4. [Introduction to Docker Compose](#introduction-to-docker-compose)
5. [Debugging and Inspection](#debugging-and-inspection)
6. [System Maintenance](#system-maintenance)
7. [Contributing](#contributing)
8. [Resources](#resources)

---

## Building Images

Docker images are blueprints for containers. These commands help you build, manage, and distribute images.

- **Build an Image from a Dockerfile**
  ```bash
  docker build -t <image-name>:<tag> .
  ```
  This command builds a new Docker image from the instructions in a `Dockerfile`. The `-t` flag tags the image with a name and optional tag. The `.` specifies the build context (the current directory).

- **List Docker Images**
  ```bash
  docker images
  ```
  Displays a list of all Docker images on your system, including their repository, tag, and size.

- **Remove a Docker Image**
  ```bash
  docker rmi <image-name>
  ```
  Removes a specified image from your local repository. You may need to remove all containers using the image before the image can be removed.

- **Pull an Image from a Registry**
  ```bash
  docker pull <image-name>:<tag>
  ```
  Downloads a Docker image from a public or private registry (like Docker Hub).

---

## Dockerfile Basics

A `Dockerfile` is a text document that contains all the commands a user could call on the command line to assemble an image. Here are some of the most common instructions:

- **`FROM`**: Specifies the base image to build upon.
  ```Dockerfile
  FROM ubuntu:20.04
  ```

- **`WORKDIR`**: Sets the working directory for subsequent instructions.
  ```Dockerfile
  WORKDIR /app
  ```

- **`COPY`**: Copies files from the host to the container's filesystem.
  ```Dockerfile
  COPY . .
  ```

- **`RUN`**: Executes a command during the build process.
  ```Dockerfile
  RUN apt-get update && apt-get install -y python3
  ```

- **`CMD`**: Provides the default command to execute when a container starts.
  ```Dockerfile
  CMD ["python3", "app.py"]
  ```

- **`EXPOSE`**: Informs Docker that the container listens on the specified network ports at runtime.
  ```Dockerfile
  EXPOSE 5000
  ```

---

## Managing Containers

Containers are running instances of Docker images. Here are the essential commands for managing their lifecycle.

- **Run a Container**
  ```bash
  docker run [OPTIONS] <image-name>
  ```
  Creates and starts a new container from an image.
  - `--name <container-name>`: Assign a custom name.
  - `-d`: Run in detached mode (in the background).
  - `-p <host-port>:<container-port>`: Map a port from the host to the container.
  - `--rm`: Automatically remove the container when it exits.
  - `-it`: Create an interactive terminal session.

- **List Containers**
  ```bash
  docker ps
  ```
  Shows a list of all currently running containers.
  - `-a`: Show all containers, including stopped ones.

- **Stop a Container**
  ```bash
  docker stop <container-name-or-id>
  ```
  Stops a running container gracefully.

- **Start a Container**
  ```bash
  docker start <container-name-or-id>
  ```
  Starts a stopped container.

- **Remove a Container**
  ```bash
  docker rm <container-name-or-id>
  ```
  Deletes a stopped container. Add `-f` to force-remove a running container.

---

## Introduction to Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications. With a single `docker-compose.yml` file, you can configure your application's services, networks, and volumes.

- **Start All Services**
  ```bash
  docker-compose up
  ```
  Builds, (re)creates, starts, and attaches to containers for a service. Add the `-d` flag to run in detached mode.

- **Stop All Services**
  ```bash
  docker-compose down
  ```
  Stops and removes containers, networks, and volumes created by `up`.

- **List Services**
  ```bash
  docker-compose ps
  ```
  Lists the containers and their status.

- **View Logs**
  ```bash
  docker-compose logs <service-name>
  ```
  Displays log output from a specific service. Use the `-f` flag to follow logs.

---

## Debugging and Inspection

These commands help you look inside your containers and understand their behavior.

- **View Container Logs**
  ```bash
  docker logs <container-name-or-id>
  ```
  Fetches the logs of a container.
  - `-f`: Follow the log output in real-time.
  - `--tail <number>`: Show the last `N` lines of the logs.

- **Execute a Command in a Running Container**
  ```bash
  docker exec -it <container-name-or-id> <command>
  ```
  Runs a command inside a running container. A common use case is starting a shell session:
  ```bash
  docker exec -it <container-name-or-id> /bin/bash
  ```

- **Inspect a Container**
  ```bash
  docker inspect <container-name-or-id>
  ```
  Returns detailed, low-level information about a container, such as its IP address, volume mounts, and configuration.

- **Monitor Resource Usage**
  ```bash
  docker stats
  ```
  Displays a live stream of resource usage statistics (CPU, memory, network I/O) for all running containers.

---

## System Maintenance

Keep your Docker environment clean and efficient with these commands.

- **Remove All Stopped Containers**
  ```bash
  docker container prune
  ```
  Deletes all stopped containers in one command.

- **Remove Unused Images**
  ```bash
  docker image prune
  ```
  Deletes all dangling images (images not tagged or associated with any container).
  - `-a`: Remove all unused images, not just dangling ones.

- **Clean Up Unused Docker Objects**
  ```bash
  docker system prune
  ```
  Removes all unused containers, networks, and dangling images.
  - `--volumes`: Also remove unused volumes.

---

## Contributing

Contributions are welcome! If you have a favorite Docker command that you think is missing, or if you have a suggestion for improving an explanation, please feel free to open a pull request.

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/add-new-command`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add new command'`).
5. Push to the branch (`git push origin feature/add-new-command`).
6. Open a pull request.

---

## Resources

For more detailed information on Docker and its usage, check out the official Docker documentation:

- [Docker Documentation](https://docs.docker.com)
- [Docker Command Line Reference](https://docs.docker.com/engine/reference/commandline/docker/)

Feel free to contribute additional commands or tips by submitting a pull request. Happy Dockering!

---
