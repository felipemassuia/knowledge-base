# Docker
###### Docker is a tool created to provide a simpler way to configure and run applications and intire simulations of operational systems trought the concept of **container**.
###### A container is an instance of an image, wich is a descriptions of a configuration to run an application. Each container is a process inside the original system and it has some characteristics to keep the integrity of it. The list below shows some of this concepts, known as "namespaces".
* **PID** Keep the isolation of the processess inside the container
* **NET** Keep the network isolation
* **IPC** Keep the isolation between process and shared memory
* **MNT** Keep the isolation of the file system
* **UTS** Keep the kernel isolation
---
### The problem
###### There is a long way trought the computing study to get to the container concept. At first, we used to run our applications directily inside a physical machine. But this kind of implementation has a big problem:
> How can I run 3 apps at the same time? (for example, a Java process running at 80 port and a Nginx at 80 too)
###### Our first attempt is to run in 2 machines, but it is very expensive and a lot of companies tried to find alternatives to this situation.
###### So, the **virtualization** born up. At the virtualization model, we can simulate separate machines with a hypervisor ledger. So now we can run our apps each one inside a VM (Virtual Machine).
###### The container model is an evolution of virtualization at the time we can remove the hypervisor ledger and run only the container with the aplication, in a ligher an faster way. They are ephemeral, isolated and configurated using images. 
<div align="center">
<img src="https://www.redhat.com/cms/managed-files/styles/wysiwyg_full_width/s3/virtualization-vs-containers_transparent.png?itok=q-E2I2-L" width="700px" />
</div>

---
### The images
###### An image is a group of layers of another images, with is a description of an app or environment. When we  create a container, we are adding an aditional layer at the top of the image, with the ability to read and write there. When we remove a container, we are removing this layer. An image can be reused by a lot of images that use this first image to create itself. This is one of the reasons that do Docker so light and fast to put working.
---
### Installing Docker
| Operational System | Guide                                                    |
|--------------------|----------------------------------------------------------|
| Windows            | https://docs.docker.com/desktop/install/windows-install/ |
| Linux              | https://docs.docker.com/desktop/install/linux-install/   |
| MacOS              | https://docs.docker.com/desktop/install/mac-install/     |

---
### Usefull commands
> docker run image-name
> ###### _(run container. If the image doesn't exists at the local repository, look foward it at the Docker Hub. Use "-d" parameter to run in detached mode. Use "-P" to expose port between container and host)_

> docker start container-id
> ###### _(Start the container)_

> docker stop container-id
> ###### _(Stop the container)_

> docker ps
> ###### _(List the containers in execution)_

> docker ps -a
> ###### _(List the containers including the stopped ones)_

> docker pull image-name
> ###### _(Download the image with no start of the container)_

> docker exec -it bash container-id
> ###### _(Run a command inside the container at the interative mode. Start a bash for example)_

> docker pause container-id
> ###### _(Pause the container)_

> docker rm container-id
> ###### _(Remove container. Use "--force" parameter to force stop before removing)_

> docker images
> ###### _(List images)_

> docker build -t user/image-name:1.0 .
> ###### _(Create image from Dockerfile)_

> docker inspect image-id
> ###### _(Show technical features about the image)_

> docker history image-id
> ###### _(Show layers that compose an image)_
---
### Creating images
###### Create an image is a task that you can configure all the process to run your app. It is a good idea to follow the docker reference to create an image as the link above shows.
> https://docs.docker.com/engine/reference/builder/
###### To create an image, you will need to create a file called "Dockerfile" (with no extension). Inside this one, you can configure some commands. The description below shows a web app that can be built using docker build command.

````
FROM note:14
WORKDIR apps/node
COPY . .
RUN NPM INSTALL
ENTRYPOINT NPM START
````
---
### Files and persistence
###### There are some ways to persist data of a container. The commands below shows some ways to do it.
<div align="center">
<img src="https://docs.docker.com/storage/images/types-of-mounts.png" width="500px" />
</div>

* Bind mount
* Volume
* Tmpfs mount

> docker run -it -v /home/volume:/app ubuntu bash
> ###### _(Create a bind mount between the "/home/volume" file and the "/app" inside the container)_

> docker run -it --mount type=bind,source=/home/volume,target=/app ubuntu bash
> ###### _(More elegant way to do the same thing)_

> docker volume ls
> ###### _(List volumes)_

> docker volume create volume-name
> ###### _(Create a volume called "volume-name")_

> docker run -it --tmpfs=/app ubuntu bash
> ###### _(Create a temporary file to be used by container)_
---
### Network
###### Docker has a mechanism to ensure the isolation of network interfaces and also the DNS communication of containers

> docker inspect container-id
> ###### _(Show container technical features)_

> docker network ls
> ###### _(Show networks technical features)_

> docker network create --driver bridge my-network
> ###### _(Create network)_
---
### Docker Compose
###### Docker compose is a tool to define multi containers environments.
###### To use this tool, create a file named docker-compose.yml
> https://docs.docker.com/compose/features-uses/

> docker-compose up
> ###### _(Run the docker-compose.yml file)_

````yml
version : '3.3'

networks:
    default-network:
        driver: bridge

volumes:
    prometheus_data:
    grafana_data:

services:
    prometheus:
        image: prom/prometheus:latest
        volumes:
            - ./config/prometheus.yml:etc/prometheus/prometheus.yml
            - prometheus_data:/prometheus
        networks:
            - default-network
        ports:
            - 9090:9090
    grafana:
        image: grafana/grafana:latest
        ports:
            - 3000:3000
        networks:
            - default-network
````
