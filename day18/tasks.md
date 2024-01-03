# Day 18 Task: Docker for DevOps Engineers

Till now you have created Docker file and pushed it to the Repository. Let's move forward and dig more on other Docker concepts.
Aj thodi padhai krte hai on Docker Compose 😃

## Docker Compose
- Docker Compose is a tool that was developed to help define and share multi-container applications.
- With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.
- Learn more about docker-compose [visit here](https://tecadmin.net/tutorial/docker/docker-compose/)

## What is YAML?
- YAML is a data serialization language that is often used for writing configuration files. Depending on whom you ask, YAML stands for yet another markup language or YAML ain’t markup language (a recursive acronym), which emphasizes that YAML is for data, not documents. 
- YAML is a popular programming language because it is human-readable and easy to understand.
- YAML files use a .yml or .yaml extension.
- Read more about it [here](https://www.redhat.com/en/topics/automation/what-is-yaml)

## Task-1

Learn how to use the docker-compose.yml file, to set up the environment, configure the services and links between different containers, and also to use environment variables in the docker-compose.yml file. 

[Sample docker-compose.yaml file](https://github.com/LondheShubham153/90DaysOfDevOps/blob/master/2023/day18/docker-compose.yaml)

<pre>
[root@node5 ~]# mkdir test1
[root@node5 ~]# cd test1
[root@node5 test1]# vim docker-compose.yml 
[root@node5 test1]# cat docker-compose.yml 
version : "3.3"
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: mysql
    ports:
      - "3306:3306"
    environment:
      - "MYSQL_ROOT_PASSWORD=test@123"
[root@node5 test1]# docker compose up -d
[+] Running 8/8
 ✔ web 7 layers [⣿⣿⣿⣿⣿⣿⣿]      0B/0B      Pulled                          22.4s 
   ✔ af107e978371 Already exists                                           0.0s 
   ✔ 336ba1f05c3e Pull complete                                           13.4s 
   ✔ 8c37d2ff6efa Pull complete                                            4.1s 
   ✔ 51d6357098de Pull complete                                            4.1s 
   ✔ 782f1ecce57d Pull complete                                            6.2s 
   ✔ 5e99d351b073 Pull complete                                            6.2s 
   ✔ 7b73345df136 Pull complete                                            9.1s 
[+] Running 3/3
 ✔ Network test1_default  Created                                          0.3s 
 ✔ Container test1-web-1  Started                                          0.1s 
 ✔ Container test1-db-1   Started                                          0.1s 
</pre>


## Task-2
- Pull a pre-existing Docker image from a public repository (e.g. Docker Hub) and run it on your local machine. Run the container as a non-root user (Hint- Use `usermod ` command to give user permission to docker). Make sure you reboot instance after giving permission to user.
- Inspect the container's running processes and exposed ports using the docker inspect command.
- Use the docker logs command to view the container's log output.
- Use the docker stop and docker start commands to stop and start the container.
- Use the docker rm command to remove the container when you're done.

## How to run Docker commands without sudo?
- Make sure docker is installed and system is updated (This is already been completed as a part of previous tasks):
- sudo usermod -a -G docker $USER 
- Reboot the machine.

For reference you can watch this [video](https://youtu.be/Tevxhn6Odc8)

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)
