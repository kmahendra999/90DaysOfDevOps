## Day 17 Task: Docker Project for DevOps Engineers.

### You people are doing just amazing in **#90daysofdevops**. Today's challenge is so special Because You are going to do DevOps project today with Docker. Are You Exited 😍

# Dockerfile

Docker is a tool that makes it easy to run applications in containers. Containers are like small packages that hold everything an application needs to run. To create these containers, developers use something called a Dockerfile.

A Dockerfile is like a set of instructions for making a container. It tells Docker what base image to use, what commands to run, and what files to include. For example, if you were making a container for a website, the Dockerfile might tell Docker to use an official web server image, copy the files for your website into the container, and start the web server when the container starts.

For more about Dockerfile visit [here](https://rushikesh-mashidkar.hashnode.dev/dockerfile-docker-compose-swarm-and-volumes)

task:

- Create a Dockerfile for a simple web application (e.g. a Node.js or Python app)

- Build the image using the Dockerfile and run the container

- Verify that the application is working as expected by accessing it in a web browser

<pre>
  Certainly! Below are the steps to create a Dockerfile for both MySQL and WordPress containers, and then build and run the containers.

1. Create directory for save data on master node:

run command on bash terminal

mkdir /blogdb

  
2. Create a Dockerfile for MySQL (Dockerfile.mysql):

# Use the official MySQL image as the base image
FROM mysql:latest

# Set environment variables
ENV MYSQL_ROOT_PASSWORD redhat
ENV MYSQL_DATABASE db_name
ENV MYSQL_USER db_user
ENV MYSQL_PASSWORD db_password

# Create a volume to persist data
VOLUME /var/lib/mysql

# Expose the default MySQL port
EXPOSE 3306

  
3. Build the MySQL image:
Navigate to the directory containing Dockerfile.mysql and run the following command:
docker build -t custom-mysql:latest -f Dockerfile.mysql .

  
4. Create a Dockerfile for WordPress (Dockerfile.wordpress):
# Use the official WordPress image as the base image
FROM wordpress:latest

# Set environment variables
ENV WORDPRESS_DB_HOST mysqlcon
ENV WORDPRESS_DB_USER db_user
ENV WORDPRESS_DB_PASSWORD db_password
ENV WORDPRESS_DB_NAME db_name

# Expose the default WordPress port
EXPOSE 80



  
5. Build the WordPress image:

Navigate to the directory containing Dockerfile.wordpress and run the following command:
docker build -t custom-wordpress:latest -f Dockerfile.wordpress .

  
6. Run the MySQL container:
docker run -dit --name mysqlcon -v /blogdb:/var/lib/mysql custom-mysql:latest

  
7. Run the WordPress container:
docker run -dit --name wpcon --link mysqlcon -p 8080:80 custom-wordpress:latest



  
Now, you have created custom Docker images for MySQL and WordPress, and you've started containers using these custom images. The -v option in the MySQL container mounts the /blogdb directory on the host to persist MySQL data. The --link option in the WordPress container establishes a link to the MySQL container.
</pre>





- Push the image to a public or private repository (e.g. Docker Hub )

<pre>
  [root@node5 ~]# docker login
Log in with your Docker ID or email address to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com/ to create one.
You can log in with your password or a Personal Access Token (PAT). Using a limited-scope PAT grants better security and is required for organizations using SSO. Learn more at https://docs.docker.com/go/access-tokens/

Username: domainindustries
Password: 
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded

[root@node5 ~]# docker tag custom-mysql:latest domainindustries/mysql-wp:latest
  
[root@node5 ~]# docker push domainindustries/mysql-wp:latest
The push refers to repository [docker.io/domainindustries/mysql-wp]
e4ee9c43adca: Mounted from library/mysql 
8bb27dddf553: Mounted from library/mysql 
bea7023e9dd9: Mounted from library/mysql 
d30c9e468341: Mounted from library/mysql 
7242463c3e84: Mounted from library/mysql 
7d6226d7a694: Mounted from library/mysql 
f8ee6fd60415: Mounted from library/mysql 
9166c8be8ddc: Mounted from library/mysql 
805c4ad62bbd: Mounted from library/mysql 
d87ce14fed78: Mounted from library/mysql 
latest: digest: sha256:89fe6e7a7fb50d3c72cbe2a3b9172d8839f950ae37faafc8aca20391de0a3473 size: 2411
  
[root@node5 ~]# docker images
REPOSITORY                  TAG       IMAGE ID       CREATED             SIZE
mycustonhttpd               latest    b9451f4b3e51   About an hour ago   167MB
vimal13/welcome             v2        5b2d1ac9e5df   7 days ago          204MB
vimal13/welcome             v1        31330db91ebe   7 days ago          204MB
mysql                       latest    73246731c4b0   2 weeks ago         619MB
domainindustries/mysql-wp   latest    ecfe1c31f183   2 weeks ago         619MB
custom-mysql                latest    ecfe1c31f183   2 weeks ago         619MB
custom-wordpress            latest    24edb931cf4e   3 weeks ago         739MB
wordpress                   latest    fd2f5a0c6fba   3 weeks ago         739MB
httpd                       latest    6fd77d7e5eb7   2 months ago        167MB
hello-world                 latest    d2c94e258dcb   8 months ago        13.3kB

[root@node5 ~]# docker tag custom-wordpress:latest domainindustries/custom-wp:latest
  
[root@node5 ~]# docker push domainindustries/custom-wp:latest
The push refers to repository [docker.io/domainindustries/custom-wp]
1864ea81492e: Mounted from library/wordpress 
69ad30b02533: Mounted from library/wordpress 
edf4b5533c54: Mounted from library/wordpress 
2bc6c6bf963c: Mounted from library/wordpress 
da50bd45aec4: Mounted from library/wordpress 
92dc213dec8e: Mounted from library/wordpress 
164503473204: Mounted from library/wordpress 
bc571d062ee0: Mounted from library/wordpress 
b3bace8598d1: Mounted from library/wordpress 
ecf8ba143574: Mounted from library/wordpress 
1053def76735: Mounted from library/wordpress 
6e71476f2417: Mounted from library/wordpress 
380941c54064: Mounted from library/wordpress 
d0b82de7a516: Mounted from library/wordpress 
a74fbcdc7b18: Mounted from library/wordpress 
5dd2e9a27d29: Mounted from library/wordpress 
20b4537eb782: Mounted from library/wordpress 
38a6e0f337b9: Mounted from library/wordpress 
a84f293bd7d4: Mounted from library/wordpress 
e51e598b299b: Mounted from library/wordpress 
7292cf786aa8: Mounted from library/httpd 
latest: digest: sha256:82f32c5902f6a89888fe29b9b5248b3c8c2f37e800ef7a30ef8f8da6ef2f9ab6 size: 4711
[root@node5 ~]# 

</pre>


For Refference Project visit [here](https://youtu.be/Tevxhn6Odc8)

If you want to dive further, Watch [bootcamp](https://youtube.com/playlist?list=PLlfy9GnSVerRqYJgVYO0UiExj5byjrW8u) 

You can share the learning with everyone over linkedin and tag us along 😃

Happy Learning:)

