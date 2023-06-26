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
- [Basic Docker Commands](#basic-docker-commands)
- [Docker Run](#docker-run)
    - [Port Mapping or Port Publishing](#port-mapping-or-port-publishing)
    - [Volume Mapping](#volume-mapping)
    - [Container Logs](#container-logs)
  - [Advanced Run Features](#advanced-run-features)
    - [Jenkins (Build System / Web Server)](#jenkins-build-system--web-server)
    - [Demo - Creating a new Docker image](#demo---creating-a-new-docker-image)
- [It was "pip install flask", but since I had to install python2 it needed changed.](#it-was-pip-install-flask-but-since-i-had-to-install-python2-it-needed-changed)
- [pip2 install flask-mysql (The demo skipped it)](#pip2-install-flask-mysql-the-demo-skipped-it)
  - [Environmental Variables](#environmental-variables)
  - [Commands vs Entrypoint](#commands-vs-entrypoint)
- [Docker Compose](#docker-compose)
  - [Docker Build](#docker-build)
- [Docker Engine, Storage](#docker-engine-storage)
- [Networking](#networking)
- [Registry](#registry)
- [Docker on Mac and Windows](#docker-on-mac-and-windows)
- [Container Orchestration - Docker Swarm and Kubernetes](#container-orchestration---docker-swarm-and-kubernetes)
- [Conclusion](#conclusion)
- [Relevant Links](#relevant-links)


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

# Basic Docker Commands

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

# Docker Run

Run specific versions of an image with a tag. It is the image name separaged by a colon and version. (Ex. docker run redis:4.0) If no tag is specified Docker will consider the default tag "latest".

By default a Docker container does not listen to standard input. It runs in a non-interactive mode. To use interactive mode you must specify the -i parameter.

**Example:**
```
docker run -i kodekloud/simple-prompt-docker
Also, to use a sudo-terminal use -it as such.
docker run -i kodekloud/simple-prompt-docker
```

Use the --name "{Container Name} to assign a name to the container. **Note the two dashes**

### Port Mapping or Port Publishing

- docker run -p 80:5000 kodekloud/webapp (This would map to the local IP)

To get the container IP run the following command: (Returns information in a JSON format.)

```
docker inspect \
  -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' {container_name_or_id}
```

To check the port mapping run "docker por {ID}".

### Volume Mapping

Containers have their own isolated filesystem and all data stored is located inside the container. Therefore, if you remove and recreate the container all the data is lost. It is not persistent. If you would like the data to persist you would have to map the directory to a location outside the container.

**Example:**
```
docker run -v /opt/datadir:/var/lib/mysql mysql (-v {local path}:{internal path})
```

To get additional details about a container that the docker ps command us "docker inspect {Container Name or ID}".

### Container Logs

On a running instance use the "docker logs {Container Name or ID}" command.

**Note:**
```
Use the "docker run jenkins/jenkins" command and not "docker run jenkins" command which is now depreciated.
```

## Advanced Run Features

- docker run ubuntu cat /etc/*release* (Runs the container and shows version)
- docker attach {Container Name or ID} will bring the container back into the forground. Not sure why you would want that.

### Jenkins (Build System / Web Server)

1. docker run jenkins/jenkins
2. Run docker ps from another console
3. It may be accessed by the host IP or a mapped port
4. To find the internal IP address of the container run "docker inspect {Container Name or ID}". Used from host. The local port can be verified listening with the netstat -aon from the command shell.
5. connect to http:/127.0.0.1:8080

**Note: Persistent Storage**
```

docker run -d -p 8080:8080 -p 50000:50000 --restart=on-failure -v jenkins_home:/var/jenkins_home jenkins/jenkins

Access is http://127.0.0.1:8080

Note:
The /var/lib/docker/volumes/jenkins_home directory will be the actual configuration data store for the named volume.
```


**Creating an Image:**
1. Create a Docker file named Dockerfile. Everything in caps on the very left are **Instructions** and every thing in lower-case are **Arguments**. Every Docker image that is created must be based off of another image. Either an Operating System or a previously created image.

**Example:**
```
FROM Ubuntu

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY ./opt/source-code

ENTRYPOINT FLASK_API=/opt/source-code/app.py flask run
```
1. Run the Build command and specify the Docker file and tag name for the image. This will make it available locally on your system. All Docker files must start with the **RUN** instruction.

**Example:**
```
docker build Dockerfile -t mmumshad/my-custom-app
```
2. To make it available on the Docker Hub registry run the push command and specify the name of the image you just created.

**Example:**
```
docker push mmumshad/my-custom-app
```
Docker is built in a layered architecture. Each layer only stores the changes from the previous layer. To see the history run the **docker history {registry/image name}** command. When you run the **docker build .** command you will see the steps run and their status. All steps are cashed so if one layer fails and you fix it when you re-run the docker build command it will skip the completed layers. The same is true when you add additional steps in the docker file. This way, rebuilding the image is faster and you don't have to wait for Docker to rebuild the entire image each time. When you update your code, only the layers above the existing layers need built.

**Note:**
```
You can containerize just about everything.
```

### Demo - Creating a new Docker image

- [mmumshad/simple-webapp-flask](https://github.com/mmumshad/simple-webapp-flask)

* From within docker perform the following steps 

**Note:**
```
Map port if run from windows
```

1. docker run -it ubuntu bash (-it is "Standard input" and "terminal".)
2. apt-get update (This will pull Python)
3. apt-get -y install python3

```
Note:
Need to get python3 working. It was originally just supposed to cal python, but throws an error.
```
4. apt-get install python-pip
5. pip2 install flask
# It was "pip install flask", but since I had to install python2 it needed changed.
# pip2 install flask-mysql (The demo skipped it)
6. cat > opt/app.py (Cut and paste code then Ctrl+C to exit)
7. cd opt
8. FLASK_APP=app.py flask run --host=0.0.0.0
9. From host run http://172.17.0.2:5000
10.  From host run http://172.17.0.2:5000/how are you

So basically:

1. Make a working directory
2. Run through the code manually to make sure it works
3. Run history and copy the code into a docker file.
4. Run "docker build . -t {Tag Name}" to build the image

**Pushing to:**

- Login to Docker Hub: docker login
- docker push dockoftheday/{Image Name}

## Environmental Variables

Variables can be set at the OS level and changed at the CLI as well.

**Example:**
```
Within the app code.

color = os.environ.get('APP_COLOR')

Set in the OS.

export APP_COLOR=blue; python app.

From the CLI to override.

docker run -e APP_COLOR=red simple-webapp-color 
```

To find the docker veriables us the docker inspect {Image Name / ID}.


## Commands vs Entrypoint



**Example:**
```
# Install Nginx.

RUN \
  add-apt-repository -y ppa:nginx/stable && \
  apt-get update && \
  apt-get install -y nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx

  # Define mountable directories.
  
  VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/con....

  # Define working directory.

  WORKDIR /etc/nginx

  # Define default command.

  CMD ["nginx"]

```

Two formats for running the command within the image.

- CMD command param1 (Standard Standard)
- CMD ["command", "param1"] (JSON Format)

THe ENTRYPOINT instruction specifies the command that will be run when the container starts. 

**Example:**
```
FROM Ubuntu

ENTRYPOINT ["sleep"]

CMD ["5"] (Would set a default)

To override simply run:
docker run {sleeper image} 10
```

Also, the entrypoing can be overridden as such:
```
docker run --entrypoint sleep2.0 ubuntu-sleeper 10
```

# Docker Compose

A better way to configure and run multiple services than multiple **docker run** commands using a docker-compose.yml file format.

Running a **docker-compose up** command is easier to implement, run, and maintain as all configuration changes are always stored in the docker-compose configuration file. However, this is only applicable to running the multiple services on a single Docker host.

** Sample Application: Voting application**

- voting-app (Python)
- in-memory db (Redis)
- worker (.NET application)
- db (PostgreSQL / table of cat & dog totals)
- result-app (Node.js)

 Docker run --links tells a container to reference another container service by name.

 **Example: (Legacy)**
 ```

docker run -d --name=redis redis

docker run -d --name=db postgres:9.4

docker run -d --name=vote -p 5000:80 --link redis:redis voting-app

docker run -d --name=result -p 5001:80 --link db:db  result-app

docker run -d --name=worker --link db:db voting-app

NOTE: Using links this way is deprecated and may be removed in future releases of Docker.
 ```

**Example: (docker-compose.yml)**
```

redis
  image: redis
db:
  image: postgres9.4
vote: 
  image: voting-app
  ports:
    - 5000:80
  links:
    - redis
result:
   result-app
   ports:
    - 5001:80
   links:
    - db
worker:
  image: worker
  links:
    - redis
    - db

NOTE: Links could also be specified in the **db:db = db** format.

```
## Docker Build

It is not necessary that all images are built. In our example three are custom and need built. to do this replace the **image: {image name}** with **build:{./image code and a Dockerfile}** instead.




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
- [How to check open ports for live streaming](https://inevent.com/blog/tech-and-trends/how-to-check-open-ports-for-live-streaming.html)
- [Docker Hub: docker/example-voting-app-vote](https://hub.docker.com/r/docker/example-voting-app-vote)
- - [Docker Hub: docker/example-voting-app-worker](https://hub.docker.com/r/docker/example-voting-app-worker)
- - [Docker Hub: docker/example-voting-app-result](https://hub.docker.com/r/docker/example-voting-app-result)