# Docker Journey
![Preview](https://brandslogos.com/wp-content/uploads/images/large/docker-logo.png)
# Learning Objectives
**Part1**
- [x] Define Docker and explain common use cases.
Understand how containers functionally and operationally differ from virtual machines.
- [x] Explore three key technologies that make Docker different: layered containers, the Dockerfile, and the Docker API.
- [x] Learn how to create and manage containers using the Docker CLI.
- [x] Understand how to create custom container images using Dockerfiles.
- [x] Learn how to push Docker images to the Docker registry and manage them.
- [x] Troubleshoot common container issues using Docker CLI commands.
- [x] Understand common best practices and problems when working with Docker containers and images. <br>

**Part2**
- [x] Understand the basics of Docker and how containers work.
- [x] Learn about Docker Engine and container runtimes, including advantages and disadvantages of different options.
- [x] Explore the Open Container Initiative and its specification on container runtimes.
- [x] Learn about the Docker daemon and its operation.
- [x] Discover how to set container limits in Docker.
- [x] Learn how to configure logging with logging drivers.
- [x] Discover important files and directories used by Docker Engine.
- [x] Learn about alternative ways to run Docker, including on a VM or within WSL.
- [x] Discover how to create Docker networks and volumes.
- [x] Understand the core components of a Docker image and how to customize images with Dockerfile commands.
- [x] Create and log into authenticated registries.
- [x] Gain an understanding of best practices for working with Docker containers and images, as well as scaling with Docker Compose and Kubernetes.

# Problem
`It's Works on My Machine` 
*Reason*:
1. Different system configuration
2. Missing files, hardware, or other properties
3. Hardware dependencies

*Previous Solution*:
- Configuration Management Tools: Chef, Puppet, Ansible (Configuration as code)
    - Require knowledge about hardware and OS
- VM as code: Vagrant
    - Heavy, show-ish, requires inconvenient configuration<br>

=> **Docker** uses **images** and **containers** to allow apps to run anywhere, consistency

# Docker Anatomy
![Docker Anatomy](https://github.com/meofiscoding/Docker-Journey/blob/main/asset/DockerAnatomy.png)
- Docker use `control groups`, `namespaces`, and `images` to make running apps anywhere easier
**Docker makes containers easy**
- Configuration through Dockerfiles, not shell commands
- Share images with others through image registries
- A supper easy command line client and API

# Container Assumption
![Container Assumption](https://github.com/meofiscoding/Docker-Journey/blob/main/asset/ContainerAssumption.png)
Container  | VM
------------- | -------------
Run in container runtimes  | - Run on top of hypervisors
Work alongside OS | - Need hardware emulation
Do not require OS configuration | - Require OS configuration
Run 1 app at a time (usually) | - Can run many app at once

# Docker best practices
:point_right: Use verify images

:point_right: Use `Container Image Scanner` to scan images if not using official images. <br>
              ***Example*** : Free open source scanner: Clair, Trivy, Dagda

:point_right: Avoid using `latest` tag because of 3 issue: <br>
    - You don't know what version of the app you are downloading<br>
    - The app's version may change without you knowing when you run `docker pull`<br>
    - `lastest` can be overriden by Docker Hub, making rollbacks difficult<br>

:point_right: Use **Non-root user** in container to ensure security of container

**If you have a web app that needs a database, web server, and cache** <br>
                :x: don't roll them into one giant Docker images <br>
                :white_check_mark: Create a bunch of containers and link them together through virtual networks and separate data volumes<br>
            => Use `docker-compose` to manage multiple containers <br>
            :point_right: With `Compose` you can use a single file called `Compose Manifest` to define all the containers you need for your app and how they should be linked together and then start them all with `docker-compose up`
# <img src="https://upload.wikimedia.org/wikipedia/labs/thumb/b/ba/Kubernetes-icon-color.svg/2110px-Kubernetes-icon-color.svg.png" style="width: 80px" /> Level up evenmore with Kubernetes 
:point_right: Kubernetes is a container orchestration tool that helps you manage multiple containers across multiple hosts

- **Kubernetes** resolve following Challenge of **Docker**:
    - Difficult to link Docker networks together across multiple hosts
    - Controlling Docker containers across multiple hosts is cumbersome
    - No built-in solution from moving containers from one host to another
    - Production concerns like scaling, load balancing, and high availability are difficult with single Docker client

