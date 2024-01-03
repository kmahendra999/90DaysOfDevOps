# Day 19 Task: Docker for DevOps Engineers

**Till now you have learned how to create docker-compose.yml file and pushed it to the Repository. Let's move forward and dig more on other Docker-compose.yml concepts.**
**Aaj thodi padhai krte hai on Docker Volume & Docker Network** 😃

# Docker-Volume
Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted.
You can also mount from the same volume and create more containers having same data.
[reference](https://docs.docker.com/storage/volumes/)

# Docker Network
Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run) together. This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed).
When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that. [reference](https://docs.docker.com/network/)


## Task-1
- Create a multi-container docker-compose file which will bring *UP* and bring *DOWN* containers in a single shot ( Example - Create application and database container )

*hints:*
- Use the `docker-compose up` command with the `-d` flag to start a multi-container application in detached mode.
- Use the `docker-compose scale` command to increase or decrease the number of replicas for a specific service. You can also add [`replicas`](https://stackoverflow.com/questions/63408708/how-to-scale-from-within-docker-compose-file) in deployment file for *auto-scaling*.
- Use the `docker-compose ps` command to view the status of all containers, and `docker-compose logs` to view the logs of a specific service.
- Use the `docker-compose down` command to stop and remove all containers, networks, and volumes associated with the application

<pre>
  [admin@node5 root]$ sudo docker compose up -d
[+] Running 6/0
 ✔ Container root-mysqlcon-2  Running                                                                                                                                                                                          0.0s 
 ✔ Container root-mysqlcon-1  Running                                                                                                                                                                                          0.0s 
 ✔ Container root-wpcon-2     Running                                                                                                                                                                                          0.0s 
 ✔ Container root-wpcon-3     Running                                                                                                                                                                                          0.0s 
 ✔ Container root-wpcon-4     Running                                                                                                                                                                                          0.0s 
 ✔ Container root-wpcon-1     Running                                                                                                                                                                                          0.0s 
[admin@node5 root]$ sudo docker ps -a
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                                   NAMES
f442bc147590   wordpress:latest   "docker-entrypoint.s…"   17 seconds ago   Up 14 seconds   0.0.0.0:8780->80/tcp, :::8780->80/tcp   root-wpcon-2
0a0a950b2967   wordpress:latest   "docker-entrypoint.s…"   17 seconds ago   Up 9 seconds    0.0.0.0:8781->80/tcp, :::8781->80/tcp   root-wpcon-3
6fdb779adb9c   wordpress:latest   "docker-entrypoint.s…"   17 seconds ago   Up 7 seconds    0.0.0.0:8782->80/tcp, :::8782->80/tcp   root-wpcon-4
efa550d9690b   wordpress:latest   "docker-entrypoint.s…"   17 seconds ago   Up 6 seconds    0.0.0.0:8783->80/tcp, :::8783->80/tcp   root-wpcon-1
3a2d8ddd1c08   mysql:latest       "docker-entrypoint.s…"   17 seconds ago   Up 16 seconds   3306/tcp, 33060/tcp                     root-mysqlcon-2
d4978e02b5dd   mysql:latest       "docker-entrypoint.s…"   17 seconds ago   Up 15 seconds   3306/tcp, 33060/tcp                     root-mysqlcon-1
[admin@node5 root]$ sudo cat docker-compose.yml
version: "3.3"

services:
  mysqlcon:
    image: mysql:latest
    #container_name: mysqlcon
    environment:
      - MYSQL_ROOT_PASSWORD=redhat
      - MYSQL_DATABASE=db_name
      - MYSQL_USER=db_user
      - MYSQL_PASSWORD=db_password
    volumes:
      - /blogdb:/var/lib/mysql
    # Set the initial scale for mysqlcon to 1 replica
    deploy:
      replicas: 2

  wpcon:
    image: wordpress:latest
    environment:
      - WORDPRESS_DB_HOST=mysqlcon
      - WORDPRESS_DB_USER=db_user
      - WORDPRESS_DB_PASSWORD=db_password
      - WORDPRESS_DB_NAME=db_name
    ports:
      - "8780-8783:80"
    links:
            - mysqlcon
    # Set the initial scale for wpcon to 3 replicas
    deploy:
      replicas: 4
[admin@node5 root]$ docker compose ps
stat .: permission denied
[admin@node5 root]$ sudo docker compose ps
NAME              IMAGE              COMMAND                                     SERVICE    CREATED          STATUS          PORTS
root-mysqlcon-2   mysql:latest       "docker-entrypoint.sh mysqld"               mysqlcon   10 minutes ago   Up 10 minutes   3306/tcp, 33060/tcp
root-wpcon-1      wordpress:latest   "docker-entrypoint.sh apache2-foreground"   wpcon      10 minutes ago   Up 10 minutes   0.0.0.0:8783->80/tcp, :::8783->80/tcp
root-wpcon-2      wordpress:latest   "docker-entrypoint.sh apache2-foreground"   wpcon      10 minutes ago   Up 10 minutes   0.0.0.0:8780->80/tcp, :::8780->80/tcp
root-wpcon-3      wordpress:latest   "docker-entrypoint.sh apache2-foreground"   wpcon      10 minutes ago   Up 10 minutes   0.0.0.0:8781->80/tcp, :::8781->80/tcp
root-wpcon-4      wordpress:latest   "docker-entrypoint.sh apache2-foreground"   wpcon      10 minutes ago   Up 10 minutes   0.0.0.0:8782->80/tcp, :::8782->80/tcp
[admin@node5 root]$ 

</pre>

## Task-2
- Learn how to use Docker Volumes and Named Volumes to share files and directories between multiple containers.

<pre>
keeping data on docker volume concept
docker volume create data-volume
docker run -v data-volume:/var/lib/mysql mysql

[root@node5 yum.repos.d]# docker volume ls
DRIVER    VOLUME NAME
local     data_volume

  
if volume will not created it will create automatticly.
</pre>

- Create two or more containers that read and write data to the same volume using the `docker run --mount` command.

<pre>
keeping data on parent machine /data-volume
docker run -v /data-volumne:/var/lib/mysql mysql
docker run --mount type=bind, source=/data-volume, target=/var/lib/mysql mysql
</pre>

- Verify that the data is the same in all containers by using the docker exec command to run commands inside each container.

<pre>docker attach mysqlconname</pre>

- Use the docker volume ls command to list all volumes and docker volume rm command to remove the volume when you're done.
<pre>
[admin@node5 ~]$ sudo docker volume rm data_volume
data_volume
[admin@node5 ~]$ sudo docker volume ls
DRIVER    VOLUME NAME
</pre>


## You can use this task as *Project* to add in your resume.

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)
