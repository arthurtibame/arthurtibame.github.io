---
title: "Docker Installation"
date: 2021-01-09T12:49:25+08:00
hero: /posts/data_engineer/docker/installation/docker-ar21.svg
description: Installation of docker
menu:
  sidebar:
    name: Installation
    identifier: docker-installation
    parent: docker
    weight: 1
---

## What is Docker?
[Docker](https://www.docker.com/)

> Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.

## What is Docker Engine?

Docker Engine is a client-server application with these major components:

- A server which is a type of long-running program called a daemon process (the dockerd command).
- A REST API which specifies interfaces that programs can use to talk to the daemon and instruct it what to do.
- A command line interface (CLI) client (the docker command).
  
![](https://docs.docker.com/engine/images/engine-components-flow.png)

## What is Container?

![](https://www.docker.com/sites/default/files/d8/styles/large/public/2018-11/container-what-is-container.png)

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. 
Docker containers that run on Docker Engine:

- Standard: Docker created the industry standard for containers, so they could be portable anywhere
- Lightweight: Containers share the machine’s OS system kernel and therefore do not require an OS per application, driving higher server efficiencies and reducing server and licensing costs.
- Secure: Applications are safer in containers and Docker provides the strongest default isolation capabilities in the industry


## Requirements
- Ubuntu (recommanded)
- Windows
- MacOS

---

#### Step 1.
```shell
$ sudo apt update && \
$ sudo apt install -y docker.io
```
#### Step 2.
```shell
$ sudo systemctl start docker.service
$ sudo systemctl enable docker.service
```
#### Step 3. check whether it is running or not
```shell
$ docker run hello-world
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```




