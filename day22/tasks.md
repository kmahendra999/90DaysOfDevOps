# Day-22 : Getting Started with Jenkins 😃

**Linux, Git, Git-Hub, Docker finish ho chuka hai to chaliye seekhte hai inko deploy krne ke lye CI-CD tool:**

## What is Jenkins?
- Jenkins is an open source continuous integration-continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.

- Jenkins is a tool that is used for automation, and it is an open-source server that allows all the developers to build, test and deploy software. It works or runs on java as it is written in java. By using Jenkins we can make a continuous integration of projects(jobs) or end-to-endpoint automation.

- Jenkins achieves Continuous Integration with the help of plugins. Plugins allow the integration of Various DevOps stages. If you want to integrate a particular tool, you need to install the plugins for that tool. For example Git, Maven 2 project, Amazon EC2, HTML publisher etc.

**Let us do discuss the necessity of this tool before going ahead to the procedural part for installation:** 
- Nowadays, humans are becoming lazy😴 day by day so even having digital screens and just one click button in front of us then also need some automation. 

- Here, I’m referring to that part of automation where we need not have to look upon a process(here called a job) for completion and after it doing another job. For that, we have Jenkins with us.

Note: By now Jenkins should be installed on your machine(as it was a part of previous tasks, if not follow [Installation Guide](https://youtu.be/OkVtBKqMt7I))

 
## Tasks: 

**1. What you understood in Jenkin, write a small article in your own words (Don't copy from Internet Directly)**
<pre>
 - Introduction: In the ever-evolving landscape of software development, efficiency and automation play pivotal roles in ensuring smooth workflows and timely releases. Jenkins, an open-source automation server, has emerged as a powerful tool for developers to automate various aspects of the software development lifecycle. This article explores the fundamental aspects of Jenkins and its contributions to streamlining development processes.
 - Understanding Jenkins: At its core, Jenkins is a continuous integration and continuous delivery (CI/CD) tool designed to automate the building, testing, and deployment of software. Developers utilize Jenkins to create pipelines, a series of automated steps that facilitate the seamless integration of code changes into a shared repository. This not only enhances collaboration among development teams but also mitigates the risk of integration errors.

 
 - Key Features of Jenkins:
    - Automated Builds: Jenkins enables the automatic building of code from source control, ensuring that the latest changes are compiled and validated regularly.
    - Continuous Integration: Developers can integrate their code changes into a shared repository multiple times a day, allowing for early detection of integration issues.
    - Testing Automation: Jenkins supports the integration of automated testing tools, enabling the execution of various tests (unit, integration, and acceptance tests) as part of the continuous integration process.
    - Deployment Automation: With Jenkins, developers can automate the deployment process, ensuring that the application is consistently and reliably deployed to various environments.
    - Extensibility: Jenkins boasts a vast ecosystem of plugins, providing flexibility and allowing developers to integrate it with other tools and technologies commonly used in their workflows.

 - Benefits of Jenkins:
    - Improved Collaboration: Jenkins promotes collaboration among development teams by providing a centralized platform for continuous integration and delivery.
    - Early Issue Detection: By automating builds and tests, Jenkins helps identify and address issues early in the development process, reducing the likelihood of defects in the final product.
    - Time and Cost Savings: Automation of repetitive tasks leads to time and cost savings, allowing developers to focus on more critical aspects of the software development process.
    - Consistent Deployments: Jenkins ensures consistency in deployments, reducing the risk of configuration errors and enhancing the reliability of the application.
 - Conclusion: In conclusion, Jenkins has become an indispensable tool in the software development toolkit, empowering teams to adopt agile practices and accelerate the delivery of high-quality software. Its automation capabilities, extensibility, and support for continuous integration and delivery make it a valuable asset for organizations striving to stay competitive in today's fast-paced development landscape. By integrating Jenkins into their workflows, developers can foster collaboration, enhance efficiency, and ultimately deliver robust software solutions to meet the demands of modern software development.
</pre>

**2.Create a freestyle pipeline to print "Hello World!!**
Hint: Use link for [Article](https://www.geeksforgeeks.org/what-is-jenkins)

Don't forget to post your progress on Linkedin. Till then Happy learning :) 


### Settingup java 11
<code>java -version
yum install java-11-openjdk-devel java-11-openjdk -y
++++++++++++++++++++++++++++++++++++++++++++++++
sudo alternatives --config java
alternatives --config javac
#java -version
#echo $JAVA_HOME
++++++++++++++++++++++++++++++++++++++++++++++++
update-alternatives --config java
**copy the java path from output
++++++++++++++++++++++++++++++++++++++++++++++++
vim ~/.bash_profile
ADD in LAST :
JAVA_HOME="/usr/lib/jvm/java-11-openjdk-11.0.18.0.10-2.el8_7.x86_64/bin/java"

or run : echo 'JAVA_HOME="/usr/lib/jvm/java-11-openjdk-11.0.21.0.9-2.el9.x86_64/bin/java"' >> ~/.bash_profile

source ~/.bash_profile
#echo $JAVA_HOME

++++++++++++++++++++++++++++++++++++++++++++++++


Refrence : https://sysadminxpert.com/steps-to-upgrade-java-8-to-java-11-on-centos-7/
</code>


### install repo of jenkins

<code>#yum install wget -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo dnf upgrade
</code>

# Add required dependencies for the jenkins package
<code>#sudo dnf install fontconfig java-17-openjdk
sudo dnf install jenkins
sudo systemctl daemon-reload
systemctl enable --now jenkins
</code>

<code>firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload
</code>

<code>#!/bin/bash
sudo yum install java-11-openjdk-devel java-11-openjdk wget -y
sudo alternatives --config java <<< 1
sudo alternatives --config javac <<< 1
echo 'export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-11.0.21.0.9-2.el9.x86_64"' >> ~/.bash_profile
source ~/.bash_profile
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo dnf upgrade -y
sudo dnf install jenkins -y
sudo systemctl daemon-reload
sudo systemctl enable --now jenkins
</code>

/var/lib/jenkins/secrets/initialAdminPassword for get admin user default password if i not create any user and skip


## Chagne port from 8080 to xxxx
<code>vim /usr/lib/systemd/system/jenkins.service 
line no 67 arround

---------------
cat -n /usr/lib/systemd/system/jenkins.service | grep PORT
    67  Environment="JENKINS_PORT=80"
    76  Environment="JENKINS_HTTPS_PORT=443"
    93  #Environment="JENKINS_HTTP2_PORT="

---------------


sudo systemctl daemon-reload
systemctl restart jenkins
</code>

Get the password from 

<code>/var/lib/jenkins/secrets/initialAdminPassword</code>

open url in browser http://192.168.29.35:9999/

Documentation : https://www.tecmint.com/install-jenkins-on-centos-8/#attachment_34899

Enter pasword >> Install suggested plugins >> Create first admin user >> setup url >> Start using jenkins

Then setup pipeline as given instructions on url : https://www.geeksforgeeks.org/what-is-jenkins/#GFG_AD_gfg_outstream_incontent


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Creating a first testing job of printing hello world in jenkins.

Install and open jenkins in gui window.

On Dashboard click on new item >> Give name 'myfirst job in jenkins' >> select freestyle project >> save/OK

You can give description (optional) 

go in Build Steps >> ADd build step >> Execute Shell >> in box write command <code>echo 'Hello world'</code>

Then save it.

after it go to job and build. and in console output you can see the result.
