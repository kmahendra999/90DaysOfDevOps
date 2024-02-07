# Day 9 Task: Deep Dive in Git & GitHub for DevOps Engineers.

## Find the answers by your understandings(Shoulden't be copied by internet & used hand-made diagrams)  of below quistions and Write blog on it.
1) What is Git and why is it important?
   
Git is a distributed version control system used for tracking changes in source code during software development. It allows multiple developers to collaborate on a project simultaneously. Git is important because it:

Tracks Changes: Git keeps a record of changes made to source code, enabling developers to revert to previous versions if needed.

Facilitates Collaboration: Multiple developers can work on the same project concurrently, merging their changes seamlessly.

Branching and Merging: Git allows developers to create branches for separate features or bug fixes. These branches can later be merged back into the main codebase.

Distributed Development: Git allows developers to work offline, independently, and later synchronize their changes with others. This decentralization enhances flexibility.

History and Accountability: Git maintains a detailed history of changes, providing insight into who made what changes and when, aiding in debugging and accountability.

Open Source: Git is open source, making it freely available and widely adopted in the software development community.

In summary, Git is crucial for efficient and collaborative software development, providing a robust framework for version control and team collaboration.



************************************


2) What is difference Between Main Branch and Master Branch??
   
The "main" branch and the "master" branch in Git essentially serve the same purpose and are used interchangeably. The difference is mainly in the naming convention.

Master Branch: Historically, "master" was commonly used as the default name for the main branch in Git repositories.

Main Branch: In recent years, there has been a shift towards using "main" instead of "master" to avoid language that may have negative historical connotations. This change is part of an ongoing effort in the tech community to promote inclusive language.

In summary, both "main" and "master" branches represent the primary branch of a Git repository where the main development work occurs. The choice between them is largely a matter of naming preference, and both are widely used in practice.


************************************



3) Can you explain the difference between Git and GitHub?
   Git: Git is a version control system that tracks changes in source code during software development. It allows multiple developers to collaborate on a project, tracks changes, facilitates branching and merging, and provides a history of modifications.

GitHub: GitHub, on the other hand, is a web-based platform that uses Git for version control. It provides a graphical interface, hosting for Git repositories, collaboration tools, and additional features like issue tracking and pull requests. GitHub is a platform for hosting and sharing Git repositories, making collaboration easier.

In essence, Git is the version control system itself, while GitHub is a hosting service and platform built around Git to enhance collaboration and provide additional tools for developers.


************************************


4) How do you create a new repository on GitHub?
Login: Log in to your GitHub account.

Navigate to Repositories: On the GitHub homepage, click on the "+" icon at the top right and select "New repository."

Fill in Repository Details:

Enter a name for your repository.
Add a description (optional).
Choose public or private visibility.
Initialize with a README file if you want to start with an initial file.
Create Repository: Click the "Create repository" button.

Your new repository is now created on GitHub! You can then clone the repository to your local machine, add files, and use Git commands to manage version control.


************************************





5) What is difference between local & remote repository? How to connect local to remote? 
Create a Remote Repository:

On GitHub, create a new repository.
Initialize Git Locally:

 - On your local machine, navigate to your project folder using the command line.
 - Run git init to initialize a Git repository locally.

Link Local to Remote:


 - Use the command: git remote add origin <remote-repository-url>
 - This connects your local repository to the remote one on GitHub.
 - Push Changes:

Make changes locally, commit them (git commit), and then push them to the remote repository using git push origin main (replace "main" with your branch name).

Now, your local and remote repositories are connected, allowing you to synchronize changes between them.



************************************




## Tasks
task-1: 
- Set your user name and email address, which will be associated with your commits.
To set your Git username and email address for commits:

bash

 - <code>git config --global user.name "Mahendra Kumar"</code>
 - <code>git config --global user.email "user@domain.com"</code>

 - Replace "Your Name" with your actual name and "your.email@example.com" with your actual email address. This configuration is applied globally, meaning it will be used for all your Git repositories on the current machine.


************************************



task-2: 
- Create a repository named "Devops" on GitHub
- Connect your local repository to the repository on GitHub.
- Create a new file in Devops/Git/Day-02.txt & add some content to it
- Push your local commits to the repository on GitHub

Sure, here are the steps for the tasks:

Create a Repository on GitHub:

Go to GitHub and create a new repository named "Devops."
Connect Local Repository to GitHub:

Open your terminal/command prompt and navigate to your local project folder.
Use the following commands:
bash
<code>
git init
git remote add origin https://github.com/kmahendra999/90DaysOfDevOps.git
</code>
Create and Add Content to a New File:

Create a new file: Devops/Git/Day-02.txt
Add content to the file.
Commit and Push to GitHub:

In the terminal, run the following commands:
bash
<code>
git add .
git commit -m "Add Day-02.txt file"
git push -u origin main
</code>
Replace "main" with your branch name if different.
Now, your local changes are pushed to the "Devops" repository on GitHub.


************************************





reff :- https://youtu.be/AT1uxOLsCdk


Note: These steps assume that you have already installed Git on your computer and have created a GitHub account. If you need help with these prerequisites, you can refer to the [day-08](https://github.com/LondheShubham153/90DaysOfDevOps/blob/ee7c53f276edb02a85a97282027028295be17c04/2023/day08/tasks.md)
