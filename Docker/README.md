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







