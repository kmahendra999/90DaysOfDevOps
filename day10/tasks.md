# Day 10 Task: Advance Git & GitHub for DevOps Engineers.

## Git Branching
 Use a branch to isolate development work without affecting other branches in the repository. Each repository has one default branch, and can have multiple other branches. You can merge a branch into another branch using a pull request.

 Branches allow you to develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository.

## Git Revert and Reset
 Two commonly used tools that git users will encounter are those of git reset and git revert . The benefit of both of these commands is that you can use them to remove or edit changes you’ve made in the code in previous commits.

## Git Rebase and Merge
 ### What Is Git Rebase?

 Git rebase is a command that lets users integrate changes from one branch to another, and the logs are modified once the action is complete. Git rebase was developed to overcome merging’s shortcomings, specifically regarding logs.

 ### What Is Git Merge?

 Git merge is a command that allows developers to merge Git branches while the logs of commits on branches remain intact.

 The merge wording can be confusing because we have two methods of merging branches, and one of those ways is actually called “merge,” even though both procedures do essentially the same thing.

 Refer to this article for a better understanding of Git Rebase and Merge [Read here](https://www.simplilearn.com/git-rebase-vs-merge-article)


## Task 1:
 Add a text file called version01.txt inside the Devops/Git/ with “This is first feature of our application” written inside. 
 This should be in a branch coming from `master`, 
 [hint try `git checkout -b dev`], 
 swithch to `dev` branch ( Make sure your commit message will reflect as "Added new feature").
 [Hint use your knowledge of creating branches and Git commit command]

****
At First we will create new Repository with name DevOps in our github.

Then in our local computer we will go to a folder and open git bash/cli.

<code>git init</code>

<code>git pull https://github.com/kmahendra999/DevOps.git</code>

<code>mkdir -p ./Devops/Git</code>

<code>echo "This is first feature of our application" > ./Devops/Git/version01.txt</code>

then we will create and change our branch to dev

<code>git checkout -b dev </code>

****


 - version01.txt should reflect at local repo first followed by Remote repo for review.
 [Hint use your knowledge of Git push and git pull commands here] 

***
<code>git remote add origin https://github.com/kmahendra999/Devops.git</code>

<code>git add .</code>

<code>git commit -m "My initial commit"</code>

<code>git push https://github.com/kmahendra999/DevOps.git</code>

***

 Add new commit in `dev` branch after adding below mentioned content in Devops/Git/version01.txt:
 While writing the file make sure you write these lines
 
 - 1st line>>  This is the bug fix in development branch
 - Commit this with message “ Added feature2 in development branch”
***
<code>echo "This is the bug fix in development branch" > ./Devops/Git/version01.txt</code>

<code>git add .</code>

<code>git commit -m "Added feature2 in development branch"</code>

<code>git push https://github.com/kmahendra999/DevOps.git</code>

***
 
 - 2nd line>> This is gadbad code
 - Commit this with message “ Added feature3 in development branch

***
<code>echo "This is gadbad code" >> ./Devops/Git/version01.txt</code>

<code>git add .</code>

<code>git commit -m "Added feature3 in development branch"</code>

<code>git push https://github.com/kmahendra999/DevOps.git</code>

***
 
 - 3rd line>> This feature will gadbad everything from now.
 - Commit with message “ Added feature4 in development branch

***
<code>echo "This is gadbad code" >> ./Devops/Git/version01.txt</code>

<code>git add .</code>

<code>git commit -m "Added feature4 in development branch"</code>

<code>git push https://github.com/kmahendra999/DevOps.git</code>

***

 Restore the file to a previous version where the content should be “This is the bug fix in development branch”
 [Hint use git revert or reset according to your knowledge]

***
<code>git log</code>

<code>git revert 532ce58e</code>

there may be conflicts.

resolve in file mannually.

<code>git add .</code>

<code>git revert --continue</code>

***
### working with git reset command
 <code>#add a file names.txt and push to remote
git init
git branch -M dev
git remote add origin https://github.com/kmahendra999/DevOps.git
vim names.txt
git add .
git commit -m "my initial commit"
git status
git push -u origin dev
git log
#add some files and deleted a file by mistake for test reset command
touch {a..g}
rm names.txt
git status
#commit the chnages by mistake done
git add .
git commit -m "file deleted by mistake and added {a..g}"
git log
#reset the chantges on #add a file names.txt and push to remote
git reset 5680c7d326bb9e7423ea006931a5bbe39eacdbcd
git log
git status</code>
***

## Task 2:

 - Demonstrate the concept of branches with 2 or more branches with screenshot.
 - add some changes to `dev` branch and merge that branch in `master`
 - as a practice try git rebase too, see what difference you get.

***
<code>git log</code>

***

## Note: 
We should learn and follow the [best practices](https://www.flagship.io/git-branching-strategies/) , industry follows for branching.

Simple Reference on branching: [video](https://youtu.be/NzjK9beT_CY)

Advance Reference on branching : [video](https://youtu.be/7xhkEQS3dXw)

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)
