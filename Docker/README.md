**1. What is container ?**
- A way of package application with all the necessary dependencies and configuration 
- Portable artifact , easily shared and moved around
- Makes development and deployment easy
- We can run different versions of same applications on the same host

**2. Where do containers live ?** 
- Private registry 
- Public registry (**hub.docker.com**)

**3. What is a container ?**
- It is a layer of images
- If one layer is already downloaded it won't download again 
- `docker run postgres:16`

**4. Difference between container and image ?**
- If the image is running then it is container - actually the application inside the docker image is running
- If it is just lying around then it is image - it is the artifact that is easily movable

**5. Difference b/w Oracle VM operation-system and docker ?**
- Hardware -> OS Kernel -> Applications
- Docker virtualizes the application layer or other application installed on top of it , it uses the kernel as host
- Whereas Oracle virtualizes the OS Kernel and the application layers

**6. Installation of Docker**
- Follow the instruction on the official website

**7. Basic Commands**
- `docker pull redis` # pull docker image
- `docker images` # list docker images
- `docker run redis` # run a redis container
- `docker ps`  # check docker running containers
- `docker -d redis:latest` # run docker images in detached mode
- `docker stop <container id>`
- `docker start <container id>`
- `docker ps -a` # show all the containers (exited ones as well)
- Even if we run the same application twice there will be no port conflicts, as there is port binding from the host machine
- `docker run -p6000:6379 -d redis` # then you can access redis service from the local
- `docker run -d -p6000:6379 --name myredis redis:latest`
- `docker logs <containerid>`
- `docker logs <container name>`
- `docker exec -it <container id> /bin/bash`

**8. Docker Network**
- `docker network ls`
- `docker network create <networkname>`
- `docker run -p6000:6379 -d --name container_name --net mynetwork image_name`

**9. Docker Compose**
- If more docker containers are need to be created , need to be communicated with each other, then we can use docker compose to structure that
- `docker run -p 8080:8080 --name mangodb -e USERNAME=hemu --net default <imagename>`
```yaml
version: '3'
services:
    mangodb:
      image: <imagename>
      ports:
        - 8080:8080  # hostport: container port
      environment:
        - USERNAME=hemu
      volumes:
        - db-data:/var/lib/mysql/data   # hostvolume: containervolume
```
- Docker compose takes care of creating common network
- When you delete the containers with the same file then automatically the network will also get deleted
- `docker-compose -f above_file.yaml up` 
- `docker-compose -f above_file.yaml down`

**10. Docker file**
```Docker
FROM node
ENV USERNAME=hemu
ENV PASSWORD=test@123
RUN mkdir -p /home/app
COPY . /home/app
CMD ['node','servers.js']
```
- docker build -t my-app:1.0 .

**11. Push images to private registry**
- Build image
- docker login with the registry creds 
- tag the image with registry tag
- push the image

**12. Docker Volumes**
- If there is no Docker volumes data will be gone when ever the docker images get restarted
- There three types of docker volumes
  1. Host Volumes
  2. Anonymous volume
  3. Named Volumes

- `docker run -p 6000:123 -d --name <container-name> -v data-db:/container/volue/ <image-name>`




