# Day 23 Task: Jenkins Freestyle Project for DevOps Engineers.

 The Community is absolutely crushing it in the #90daysofdevops journey. Today's challenge is particularly exciting as it entails creating a Jenkins Freestyle Project, an opportunity for DevOps engineers to showcase their skills and push their limits. Who's ready to dive in and make it happen? 😍

## What is CI/CD?
- CI or Continuous Integration is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently into the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration.
  The key goals of Continuous Integration are to find and address bugs quicker, make the process of integrating code across a team of developers easier, improve software quality and reduce the time it takes to release new feature updates. 


- CD or Continuous Delivery is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time. 

## What Is a Build Job?
A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.

Jenkins supports several types of build jobs, such as freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organization folders.

## What is Freestyle Projects ?? 🤔
A freestyle project in Jenkins is a type of project that allows you to build, test, and deploy software using a variety of different options and configurations. Here are a few tasks that you could complete when working with a freestyle project in Jenkins:


# Task-01
- create a agent for your app. ( which you deployed from docker in earlier task)
  <pre>
   Create A instance on aws for jenkins.
   Create another instance on aws of docker.

   on docker enable password authentication by edit /etc/ssh/sshd_config
   and /etc/ssh/sshd_config.d/50-cloud-init.conf 
   and make password authnticatoin yes

   Now open jenkins >> configure it

   dashboard >> manage jenkins >> nodes >> new node >> give name >> 
   Number of executors = 2 ( ek bar me kitne build kar sakta he)
   Launch method >> launch via ssh
   Enter host
   credintials >> add jenkins
   username and password
   and save
  </pre>
- Create a new Jenkins freestyle project for your app.
  <pre>
   in jenkins go to dashboard >> New pipeline >>
   give name and select freestyle project >> ok
   in next page save. as no instruction for it in task.
  </pre>
- In the "Build" section of the project, add a build step to run the "docker build" command to build the image for the container.
- Add a second step to run the "docker run" command to start a container using the image created in step 3.
![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/54ef4f0e-7699-4dcb-bf8b-ef3cefbca129)


# Task-02
- Create Jenkins project to run "docker-compose up -d" command to start the multiple containers defined in the compose file (Hint- use day-19 Application & Database docker-compose file)
  <pre>
   Github repo : https://github.com/kmahendra999/dockercomposeday23

   Create item >> frestule
   configure steps
     Description - test
     Source Code Management - Git - Repository url : https://github.com/kmahendra999/dockercomposeday23.git
     enable ; GitHub hook trigger for GITScm polling
     Build Steps : execute shell
       sudo docker compose up -d
       sudo docker compose ps
   Save
  </pre>
- Set up a cleanup step in the Jenkins project to run "docker-compose down" command to stop and remove the containers defined in the compose file.

  ![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/10d95e80-ee0f-48c1-bf00-8c2ec9c9ba2f)

  ![image](https://github.com/kmahendra999/90DaysOfDevOps/assets/9668316/dbcc91f0-504d-46db-9ac6-247c76b90e21)

  save and then run

For Refference jenkins Freestyle Project visit [here](https://youtu.be/wwNWgG5htxs)

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange.

Happy Learning:)
