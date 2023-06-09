![docker logo](https://user-images.githubusercontent.com/31222514/232439594-66e31ac6-e1cd-4424-a173-77688e02e81b.png)

# DOCKER

## What

Docker enables consistent and portable application deployment by packaging software with its dependencies, eliminating the reliance on pre-installed components on a machine. This ensures applications run seamlessly across different environments, streamlining development, and reducing compatibility issues.

Docker is an open-source platform that automates the deployment, scaling, and management of applications by using containers. Containers are lightweight, portable, and self-sufficient units that include an application and its dependencies, allowing it to run consistently across different environments. Docker simplifies and streamlines the process of creating, packaging, and deploying applications in containers.

## Why

Docker is needed for several reasons, including:

1. Consistency: Docker containers ensure that applications run the same way, regardless of the environment they are deployed in. This consistency helps to minimize the "it works on my machine" problem, which often occurs when software behaves differently on development, testing, and production environments.

1. Portability: Docker containers can be easily moved between different systems, as they contain all the dependencies required to run the application. This portability simplifies the deployment process and makes it easier to share and distribute applications.

1. Isolation: Docker allows for better isolation between applications, as each container runs independently from the others. This isolation reduces the risk of conflicts between different applications or dependencies, making it easier to manage and maintain multiple applications on a single system.

1. Scalability: Docker facilitates horizontal scaling by making it easy to create multiple instances of a containerized application. This scalability allows for better load balancing and handling of traffic spikes, ultimately improving application performance.

1. Efficiency: Containers are generally more resource-efficient than virtual machines, as they share the host system's kernel and do not require a separate operating system for each application. This efficiency translates into lower resource usage and faster start-up times for containerized applications.

## Commands

### part 1 (docker run)

```bash

docker version

docker run <image name>

docker run <image name> command!

docker run hello-world

docker run busybox echo hi there

docker run busybox ls

docker run hello-world echo hi there

docker run hello-world ls
```

### Part 2 (docker ps)

```bash
docker ps

docker run busy-box ping google.com

docker ps

# kill (ctrl + c) the running docker

docker ps 
```

### Part 3 (create | start | stop | kill)

```bash
docker create hello-world

docker start -a hello-world

docker stop <id>

docker kill <id>
```
### Part 4 (exec -it)

```bash
docker run redis

docker exec -it <id> <command>

docker exec -it <id> redis-cli

docker exec -it <id> sh

# then, inside the shell

redis-cli

# You can exit the cli with ctrl/cmd + c
# You can exit the shell with alt/ctrl + d
```
### Part 5 (Isolation)

```bash

docker run -it busybox sh

> ls

# in another terminal

docker run -it busybox sh

> touch hello_world
> ls

# back to the first container

> ls

# we should not see the new file
```

## Docker File

The process when creating a docker file

1. Specify a base image (compares with an OS)
2. Run some commands to install all programs needed
3. Specify commands to run the container

### Creating a docker file

Create a new project.

Add a `Dockerfile`

1. Specify a base image (FROM)
2. Run some commands to install all programs needed (RUN)
3. Specify commands to run the container (CMD)

```docker
FROM alpine

# Download and install dependencies

RUN apk add --update redis

# Tell the image what to do when it starts as a container

CMD ["redis-server"]
```

Then run in the terminal

```bash
docker build .

# when you get the new id of the container

docker run <id>
```

### Build with cache
```docker
FROM alpine

# Download and install dependencies

RUN apk add --update redis
RUN apk add --update gcc

# Tell the image what to do when it starts as a container

CMD ["redis-server"]
```

## Add Docker To Our Project

```docker
FROM alpine

RUN npm install

CMD ["npm", "start"]
```

```docker
FROM node:alpine

RUN npm install

CMD ["npm", "start"]
```
We get an error when running:
```bash
docker build .
```

```bash
# ERROR

 > [2/2] RUN npm install:
#6 0.740 npm ERR! Tracker "idealTree" already exists
#6 0.741 
#6 0.741 npm ERR! A complete log of this run can be found in: /root/.npm/_logs/2023-05-11T17_25_39_283Z-debug-0.log
```

The reason is that we don't have any package.json to install

## Add Build Files

```docker
FROM node:alpine

COPY ./ ./
RUN npm install

CMD ["npm", "start"]
```
`docker build .` works
`docker run <id>` works, but we cannot reach that port

## Port Forwarding

`docker run -p 3001:3001 <id>`

## Working Directory

```docker
FROM node:alpine

WORKDIR /usr/src/app

COPY ./ ./
RUN npm install

CMD ["npm", "start"]
```

## Rebuilds

```docker
FROM node:alpine

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY ./ ./

CMD ["npm", "start"]
```

## Tag

```bash
docker build -t <tag> .
```
