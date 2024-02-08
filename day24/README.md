# Day 24 Task: Complete Jenkins CI/CD Project

Let's make a beautiful CI/CD Pipeline for your Node JS Application 😍

## Did you finish Day 23?

- Day 23 was all about Jenkins CI/CD, make sure you have done it and understood the concepts. As today You will be doing one Project End to End and adding it to your resume :)
- As you have worked with Docker and Docker compose, it will be good to use it in a live project.

# Task-01

- Fork [this](https://github.com/LondheShubham153/node-todo-cicd.git) repository:
- Create a connection to your Jenkins job and your GitHub Repository via GitHub Integration.
- Read About [GitHub WebHooks](https://betterprogramming.pub/how-too-add-github-webhook-to-a-jenkins-pipeline-62b0be84e006) and make sure you have CICD setup
- Refer [this](https://youtu.be/nplH3BzKHPk) video for the entire project

# Task-02

- In the Execute shell run the application using Docker compose
- You will have to make a Docker Compose file for this Project (Can be a good open source contribution)
- Run the project and give yourself a treat:)

For Reference and entire hands-on Project visit [here](https://youtu.be/nplH3BzKHPk)

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challenge.

Happy Learning:)

[← Previous Day](../day23/README.md) | [Next Day →](../day25/README.md)


--------------------------------------
shubham notes
<pre>
  Live DevOps Project for Resume - Jenkins CICD with GitHub Integration (Notes)

Create AWS EC2 instance
sudo apt update
    3  sudo apt install openjdk-11-jre
    4  java -version
    5  curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \   /usr/share/keyrings/jenkins-keyring.asc > /dev/null 
    6  echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \   https://pkg.jenkins.io/debian binary/ | sudo tee \   /etc/apt/sources.list.d/jenkins.list > /dev/null
    7  sudo apt-get update 
    8  sudo apt-get install jenkins
    9  sudo systemctl enable jenkins
   10  sudo systemctl start jenkins
   11  sudo systemctl status jenkins
   12  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   13  history
sudo apt install docker.io
FROM node:12.2.0-alpine
WORKDIR app
COPY . .
RUN npm install
EXPOSE 8000
CMD ["node","app.js"]
docker build . -t node-app
sudo usermod -a -G docker $USER
docker run -d --name node-todo-app -p 8000:8000 todo-node-app
Got to jenkins job
Execute shell 
docker build . -t node-app-todo
docker run -d --name node-app-container -p 8000:8000 node-app-todo

</pre>
