<h>KodeKloud: Docker Training Course for the Absolute Beginner Course</>

- [Overview](#overview)
  - [Docker makes development efficient and predictable](#docker-makes-development-efficient-and-predictable)
  - [Build](#build)
  - [Share](#share)
  - [Run](#run)
- [Introduction](#introduction)
  - [Docker Overview](#docker-overview)
  - [Getting Starting with Docker](#getting-starting-with-docker)
    - [Linux install on Windows Subsystem for Linux (WSL)](#linux-install-on-windows-subsystem-for-linux-wsl)
    - [Kali](#kali)
  - [Setup and Install Docker](#setup-and-install-docker)
- [Docker Commands](#docker-commands)
  - [Basic Docker Commands](#basic-docker-commands)
- [Docker Run](#docker-run)
- [Docker Images](#docker-images)
- [Docker Compose](#docker-compose)
- [Docker Engine, Storage](#docker-engine-storage)
- [Networking](#networking)
- [Registry](#registry)
- [Docker on Mac and Windows](#docker-on-mac-and-windows)
- [Container Orchestration - Docker Swarm and Kubernetes](#container-orchestration---docker-swarm-and-kubernetes)
- [Conclusion](#conclusion)
- [Relevant Links](#relevant-links)
  - [Training and Certification](#training-and-certification)


# Overview

- [Docker Training Course for the Absolute Beginner](https://kodekloud.com/courses/docker-for-the-absolute-beginner/)
- [Docker-for-Beginners-Mumshad-Mannambeth.pdf](https://kodekloud.com/wp-content/uploads/2021/10/Docker-for-Beginners-Mumshad-Mannambeth.pdf)
- [Join our Slack community here.](https://kodekloud.com/pages/community).
- [For any technical queries, please post them here.](https://community.kodekloud.com/c/docker-for-beginners/5?_gl=1*1yh08fr*_ga*MTgzODk1NTgwMC4xNjYxNTMxNjk4*_ga_LYL47LCHPW*MTY4NzQ5MDA4NC40MS4xLjE2ODc0OTAyMjguNjAuMC4w#_ga=2.191189481.239445548.1687047605-1838955800.1661531698).

Docker is a platform designed to help developers build, share, and run modern applications. We handle the tedious setup, so you can focus on the code.

## Docker makes development efficient and predictable
Docker takes away repetitive, mundane configuration tasks and is used throughout the development lifecycle for fast, easy and portable application development – desktop and cloud. Docker’s comprehensive end to end platform includes UIs, CLIs, APIs and security that are engineered to work together across the entire application delivery lifecycle.

## Build
- Get a head start on your coding by leveraging Docker images to efficiently develop your own unique applications on Windows and Mac.  Create your multi-container application using Docker Compose.
- Integrate with your favorite tools throughout your development pipeline – Docker works with all development tools you use including VS Code, CircleCI and GitHub.
- Package applications as portable container images to run in any environment consistently from on-premises Kubernetes to AWS ECS, Azure ACI, Google GKE and more.

## Share
- Leverage Docker Trusted Content, including Docker Official Images and images from Docker Verified Publishers from the Docker Hub repository.
- Innovate by collaborating with team members and other developers and by easily publishing images to Docker Hub.
- Personalize developer access to images with roles based access control and get insights into activity history with Docker Hub Audit Logs.

## Run 

- Deliver multiple applications hassle free and have them run the same way on all your environments including design, testing, staging and production – desktop or cloud-native.
- Deploy your applications in separate containers independently and in different languages. Reduce the risk of conflict between languages, libraries or frameworks.
- Speed development with the simplicity of Docker Compose CLI and with one command, launch your applications locally and on the cloud with AWS ECS and Azure ACI.

Hypervisors are different as they provide an abstraction layer to run various OSs on the same hardware. Whereas, Docker creates containers to run multiple systems of the dependent on the kernal version.

# Introduction

## Docker Overview

The version of OS must match the underlying OS kernal. (IE: Linux must run on Docker for Linux, and Windows Must run on Docker on Windows.)

**Docker stack:**
- The OS Software
- Docker
- OS Kernel

**Example:**

| Virtual Machine   |             | Docker Containers |             |
| :---:             | :---:       | :---:             | :---:       |
|  Application      | Application | Application       | Application |
|  Libs / Deps      | Libs / Deps | Libs / Deps       | Libs / Deps |
|  OS               | OS          |                   |             |
|  Hypervisor       |             | Docker            |             |
|                   |             | OS                |             |
|                   | Hardware    | Infrastructure    |             |

It is not a matter of either or. Multiple Docker instances can be run on top of a hypervisor.

Most operating systems and tools can be found on Docker Hub .(Docker Store)

Simply run "Docker Run {Image}" to start a container. If multiple containers are needed for the same image place a load balancer in betweeen and you can destroy and recreate them without interference.

- Docker Image: Package template plan
- Docker Containers: Running instances that are isolated with their own environment and set of processes.

## Getting Starting with Docker

- Community Edition
  - Linux
  - Mac
  - Windows
  - Cloud
- Enterprise Edition: Includes addons like Image Management, Image Security, universal control plan for managing  container orchestration.   

### Linux install on Windows Subsystem for Linux (WSL)

Alternatively, you can open a Windows Terminal and type wsl --install to install WSL if you’ve never installed it before <BR>and If you already have WSL installed on your machine, you can open Windows Terminal and type wsl --update and <BR>then type wsl --shutdown to restart WSL for the changes to take effect.

Next, you will need to install a Linux distribution, such as Ubuntu, on your Windows machine. You can do this by searching for the Microsoft Store app in the Start menu and then searching for Ubuntu. Once installed, launch the Ubuntu app.

In the Ubuntu terminal, you will need to install the X Server software. You can do this by running the command sudo apt-get install xorg to install the Xorg X Server, or sudo apt-get install xserver-xorg-core to install the Xorg X Server core package.

**Note:**
```
Run wsl -l -v to ver version of linux set to run by default.
```

### Kali

sudo apt upgrade && sudo install kali-win-kex -y
run kex to start
hit f8 and exit to close

if you run a command that needed sudo and it fails just run sudo !! and it will run the previous command.

Note:
```
sudo apt upgrade && sudo install kali-win-kex -y

zsh is installed in 24.8, but if you use a prior version run:

cp /etc/skel/.zshrc ~/

also

If an initial install is needed run:
sudo apt install zsh zsh-syntax-highlighting zsh-autosuggestions
```

use zsz
Don't need to type cd

## Setup and Install Docker

1. Remove any older versions if they exist if necessary. 
   1. sudo apt-get remove docker docker-engine docker.io containerd runc
2. Go to the [Docker Setup](https://docs.docker.com/install) page.
3. Select the appropriate Operating System version. (Linux, Mac, or Windows)
**Note:**
```
To run Windows containers, you need Windows 10 or Windows 11 Professional or Enterprise edition. Windows Home or Education editions will only allow you to run Linux containers.
```
4. Follow the instructions to install on Ubuntu Linux

# Docker Commands

- docker compose version
- docker --version
- systemctl --user start docker-desktop
- systemctl --user stop docker-desktop
- systemctl status docker
- docker ps (Shows all running containers)
- docker ps -a (Shows all containers running or not)
- docker ps stop {ID or Name} (Stops a specific container)
- docker rm {Container Name or ID} (Removes a stopped or exited container permanently)
- docker images (List all available images)
- docker rmi {Image Name} (Removes and image, but dependant containers must be deleted first)
- docker pull {image} (Will download the image, but not run it)
- docker exec (Runs commands on running containers)
- docker run -it centos bash (runs centos and put's the user in bash using -it )
- sudo -i (Change to root so sudo isn't needed for every command. Bad practice)
- sudo docker run -d --name discourse_app local_discourse/app (Name a container)
- docker-compose down (Stop the container(s))
- docker rm -f $(docker ps -a -q) (Delete all containers)
- docker volume rm $(docker volume ls -q) (Delete all volumes)
- docker-compose up -d (Restart the containers)


**Note:**
``
An Exit Status of Exited (137) what a docker stop {Container Name or Image} command. Multiple can be removed with even partial IDs such as docker rm 345 e0a  773.
``

**Example:**
```
To run a command on a running container get the info with ps -a and then run docker exec {container name or ID} cat /etc/*releas*
```

**Attach and Detach:**
 - docker run kodekloud\simple-webapp
 - docker run -d kodekloud\simple-webapp (The -d runs in detached mode.)
 - docker attach {Container name or ID} (This will reconnect to the container)

**Note:**
```
Unlike a VM, containers are not meant to host an operating system, but rather a to run a specific task or process. Once a task is complete a container will exit. It exists only as long as the process inside it is alive.
```

## Basic Docker Commands




# Docker Run


# Docker Images


# Docker Compose


# Docker Engine, Storage


# Networking



# Registry


# Docker on Mac and Windows


# Container Orchestration - Docker Swarm and Kubernetes

# Conclusion



# Relevant Links

- [KodeKloud: Docker Training Course for the Absolute Beginner](https://kodekloud.com/courses/docker-for-the-absolute-beginner/)
- [Docker Homepage](https://www.docker.com/)
- [GnuPG Homepage](https://gnupg.org/) <!-- GNU Privacy Guard-->
- [Linux curl Command Explained with Examples](https://phoenixnap.com/kb/curl-command#:~:text=curl%20\(short%20for%20%22Client%20URL,client%2Dside%20URL%20transfer%20library.) <!-- Note the escape for ( -->
- [Install Docker Desktop on Ubuntu](https://docs.docker.com/desktop/install/ubuntu/)
- [Docker: Get Started](https://docs.docker.com/get-started/)
- [Docker: Develop with Docker](https://docs.docker.com/develop/)
- [Docker Hub](https://hub.docker.com/)
- [Hashicorp Packer on Docker Hub](https://hub.docker.com/r/hashicorp/packer)
- [How to Do a Clean Restart of a Docker Instance](https://docs.tibco.com/pub/mash-local/4.3.0/doc/html/docker/GUID-BD850566-5B79-4915-987E-430FC38DAAE4.html)

## Training and Certification

- [ ] [Udemy: Building Automated Machine Images with HashiCorp Packer
](https://www.udemy.com/course/hashicorp-packer/learn/lecture/26239090#overview)