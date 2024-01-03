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

For Refference Project visit [here](https://youtu.be/Tevxhn6Odc8)

If you want to dive further, Watch [bootcamp](https://youtube.com/playlist?list=PLlfy9GnSVerRqYJgVYO0UiExj5byjrW8u) 

You can share the learning with everyone over linkedin and tag us along 😃

Happy Learning:)

