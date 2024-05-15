# Voting app

---

A simple distributed application running across multiple Docker containers.

This repository is a clone of [dockersamples/example-voting-app](https://github.com/dockersamples/example-voting-app), created for learning and experimenting with Docker containers. It serves as a practical hands-on project to understand containerization.

## Architecture

---

![Architecture diagram](images/architecture.excalidraw.png)

*Diagram from original repository.*

- **Front-end web app (Python)**: Allows users to vote between dog or cat.
- **Redis**: Acts as a queue to collect new votes.
- **Worker app (.NET)**: Consumes votes from the Redis queue and stores them in a database.
- **Postgres**: A database that stores the voting results.
- **Results web app (Node.js)**: Displays the voting results in real-time.

## Learning Objectives

---

This repository is a simplified version of the original project, with the main goals of:

- Learning Docker basics and commands.
- Building Docker images and running images available on Docker Hub.
- Setting up containers with port mapping.
- Linking containers.
- Manuall application setup.
- Automating the application setup with Docker Compose.

## Docker Basics

---

### **Containers**

- Containers are lightweight, standalone, and executable packages that include everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings.
- They are instances of Docker images that are isolated and have their own environments and set of processes.
- Unlike virtual machines, containers share the host system's kernel and resources, making them more efficient and faster to start.
- Containers are designed to run specific tasks or processes, rather than an entire operating system like virtual machines.

### **Docker Images**

- Docker images are read-only templates used to create containers. They include the application code, libraries, dependencies, and other files necessary for the application to run.
- An image can be thought of as a snapshot of a container's file system at a specific point in time.
- Images can be built from a set of instructions written in a Dockerfile, which specifies the base image, application code, and other dependencies.
- Docker images are stored in repositories, such as Docker Hub, from where they can be pulled to create new containers.

## **Some Useful Commands to Remember**

---

```bash
docker run [image]
# If the image is not available locally, it will download the image in the first run

docker ps
# List the running containers

docker ps -a
# List all running and previously stopped containers

docker stop [container id / name]
# Stop the container

docker rm [container id / name]
# Remove a container

docker images
# List images in the host

docker rmi [image]
# Remove the image from the host

docker pull [image]
# Get the image from Docker Hub

docker exec [container] [command]
# Execute a command in the Docker container

docker run -it centos bash
# Run the bash inside Centos

docker run --name [your_name] -d [image]
# Run a container with a name; -d is detach

docker run --name webapp -d nginx:1.14-alpine
# Example: Run a named container with a specific version of Nginx in detached mode

docker run [image]:[version]
# Specify a version; default is the latest version
# You can check the tags for version at Docker Hub

docker run -p [port]:[port container] [image]
# Example: docker run -p 8306:3306 mysql
# Needs port mapping

docker logs [container id / name]
# Check logs

docker inspect [container id]
# Inspect container; internal IP address
```

## Building the Voting App Manually
