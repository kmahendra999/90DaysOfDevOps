# Day 11 Task: Advance Git & GitHub for DevOps Engineers: Part-2

## Git Stash:
Git stash is a command that allows you to temporarily save changes you have made in your working directory, without committing them. This is useful when you need to switch to a different branch to work on something else, but you don't want to commit the changes you've made in your current branch yet.

To use Git stash, you first create a new branch and make some changes to it. Then you can use the command git stash to save those changes. This will remove the changes from your working directory and record them in a new stash. You can apply these changes later. <code>git stash list</code> command shows the list of stashed changes.

You can also use <code>git stash drop</code> to delete a stash and <code>git stash clear</code> to delete all the stashes.

## Cherry-pick:
Git cherry-pick is a command that allows you to select specific commits from one branch and apply them to another. This can be useful when you want to selectively apply changes that were made in one branch to another.

To use git cherry-pick, you first create two new branches and make some commits to them. Then you use <code>git cherry-pick <commit_hash></code> command to select the specific commits from one branch and apply them to the other.

## Resolving Conflicts:
Conflicts can occur when you merge or rebase branches that have diverged, and you need to manually resolve the conflicts before git can proceed with the merge/rebase.
<code>git status</code> command shows the files that have conflicts, <code>git diff</code> command shows the difference between the conflicting versions and git add command is used to add the resolved files.


# Task-01 
- Create a new branch and make some changes to it.

  <code>git init
  git branch -M dev
  git remote add origin https://github.com/kmahendra999/DevOps.git
  vim names.txt
  git add .
  git status
  git commit -m "my initial commit"
  git push -u origin dev
  git log</code>

  
  
- Use git stash to save the changes without committing them.
<pre>
User@PARAM MINGW64 /d/OneDrive/Desktop/90Days
$ git init
Initialized empty Git repository in D:/OneDrive/Desktop/90Days/.git/

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ vim names.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git add .
warning: in the working copy of 'names.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git commit -m "my initial commit names.txt created"
[master (root-commit) 332645e] my initial commit names.txt created
 1 file changed, 3 insertions(+)
 create mode 100644 names.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git log
commit 332645e77cb267c92403fdb30713c56aa247df0a (HEAD -> master)
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 13:39:12 2023 +0530

    my initial commit names.txt created

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ rm names.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git add .

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    names.txt


User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ touch {1..4}

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git add .

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   1
        new file:   2
        new file:   3
        new file:   4
        deleted:    names.txt


User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git stash
Saved working directory and index state WIP on master: 332645e my initial commit names.txt created

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git status
On branch master
nothing to commit, working tree clean

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git log
commit 332645e77cb267c92403fdb30713c56aa247df0a (HEAD -> master)
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 13:39:12 2023 +0530

    my initial commit names.txt created

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
</pre>





- Switch to a different branch, make some changes and commit them.





  <pre>
    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
    $ git branch -M desginer

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ vim designer_file.txt

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ touch design{1..4}.txt

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git add .
    warning: in the working copy of 'designer_file.txt', LF will be replaced by CRLF the next time Git touches it

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git commit -m "commit on desginer branch"
    [desginer 00d8e4b] commit on desginer branch
     5 files changed, 1 insertion(+)
     create mode 100644 design1.txt
     create mode 100644 design2.txt
     create mode 100644 design3.txt
     create mode 100644 design4.txt
     create mode 100644 designer_file.txt

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)


  </pre>


  
- Use git stash pop to bring the changes back and apply them on top of the new commits.


  <pre>
        User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git stash pop
    On branch desginer
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
            new file:   1
            new file:   2
            new file:   3
            new file:   4

    Changes not staged for commit:
      (use "git add/rm <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
            deleted:    names.txt

    Dropped refs/stash@{0} (830b0fca41569dc4b6ffeed7450fd4efe39879b3)

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git add .

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git commit -m "git stash pop command run and commit again"
    [desginer e12da58] git stash pop command run and commit again
     5 files changed, 3 deletions(-)
     create mode 100644 1
     create mode 100644 2
     create mode 100644 3
     create mode 100644 4
     delete mode 100644 names.txt

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git log
    commit e12da5802e2f513cae1bf36138d8211b98404939 (HEAD -> desginer)
    Author: kmahendra999 <k.mahendra999@hoptmail.com>
    Date:   Sun Dec 31 13:54:27 2023 +0530

        git stash pop command run and commit again

    commit 00d8e4ba10504461f4326c0713f0e30e2f76da8d
    Author: kmahendra999 <k.mahendra999@hoptmail.com>
    Date:   Sun Dec 31 13:44:20 2023 +0530

        commit on desginer branch

    commit 332645e77cb267c92403fdb30713c56aa247df0a
    Author: kmahendra999 <k.mahendra999@hoptmail.com>
    Date:   Sun Dec 31 13:39:12 2023 +0530

        my initial commit names.txt created

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
    $ git status
    On branch desginer
    nothing to commit, working tree clean

  </pre>











# Task-02
<pre>User@PARAM MINGW64 /d/OneDrive/Desktop/90Days
$ git init
Initialized empty Git repository in D:/OneDrive/Desktop/90Days/.git/

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git pull https://github.com/kmahendra999/DevOps.git
fatal: couldn't find remote ref HEAD

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ mkdir -p ./Devops/Git

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ echo "This is first feature of our application" > ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (master)
$ git checkout -b dev
Switched to a new branch 'dev'

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git remote add origin https://github.com/kmahendra999/Devops.git

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git commit -m "My initial commit"
[dev (root-commit) bfe110b] My initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git push https://github.com/kmahendra999/DevOps.git
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (5/5), 343 bytes | 343.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/kmahendra999/DevOps.git
 * [new branch]      dev -> dev

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ echo "This is the bug fix in development branch" > ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git commit -m "Added feature2 in development branch"
[dev dd4c82f] Added feature2 in development branch
 1 file changed, 1 insertion(+), 1 deletion(-)

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git push https://github.com/kmahendra999/DevOps.git
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Writing objects: 100% (5/5), 387 bytes | 387.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/kmahendra999/DevOps.git
   bfe110b..dd4c82f  dev -> dev

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ echo "This is gadbad code" >> ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git commit -m "Added feature3 in development branch"

git push https://github.com/kmahendra999/DevOps.git
[dev 114b2ea] Added feature3 in development branch
 1 file changed, 1 insertion(+)
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 24 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (5/5), 403 bytes | 403.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/kmahendra999/DevOps.git
   dd4c82f..114b2ea  dev -> dev

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ echo "This is gadbad code" >> ./Devops/Git/version01.txt

git add .

git commit -m "Added feature4 in development branch"

git push https://github.com/kmahendra999/DevOps.git
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it
[dev abee89b] Added feature4 in development branch
 1 file changed, 1 insertion(+)
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 24 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (5/5), 399 bytes | 399.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/kmahendra999/DevOps.git
   114b2ea..abee89b  dev -> dev

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git status
On branch dev
nothing to commit, working tree clean

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git log
commit abee89bb352002dadb2f6a16a78e5d6ccf9a9729 (HEAD -> dev)
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:05:35 2023 +0530

    Added feature4 in development branch

commit 114b2eaea90c231e73c9ab074371a90db1e027ab
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:05:29 2023 +0530

    Added feature3 in development branch

commit dd4c82f0be5cc677d2d5a43fe1c76ca89b53e75f
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:05:10 2023 +0530

    Added feature2 in development branch

commit bfe110b83d314bd56733f0cff1a8c6ffdae97fd6
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:04:50 2023 +0530

    My initial commit

commit abee89bb352002dadb2f6a16a78e5d6ccf9a9729 (HEAD -> dev)
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:05:35 2023 +0530

    Added feature4 in development branch

commit 114b2eaea90c231e73c9ab074371a90db1e027ab
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:05:29 2023 +0530

    Added feature3 in development branch

commit dd4c82f0be5cc677d2d5a43fe1c76ca89b53e75f
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:05:10 2023 +0530

    Added feature2 in development branch

commit bfe110b83d314bd56733f0cff1a8c6ffdae97fd6
Author: kmahendra999 <k.mahendra999@hoptmail.com>
Date:   Sun Dec 31 14:04:50 2023 +0530

    My initial commit

  
    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
    $ git revert dd4c82f0be5cc677d2d5a43fe1c76ca89b53e75f
    Auto-merging Devops/Git/version01.txt
    CONFLICT (content): Merge conflict in Devops/Git/version01.txt
    error: could not revert dd4c82f... Added feature2 in development branch
    hint: After resolving the conflicts, mark them with
    hint: "git add/rm <pathspec>", then run
    hint: "git revert --continue".
    hint: You can instead skip this commit with "git revert --skip".
    hint: To abort and get back to the state before "git revert",
    hint: run "git revert --abort".

    #'conflict resolved mannually'

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev|REVERTING)
    $ git add .

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev|REVERTING)
    $ git revert --continue
    [dev 008d622] Revert "Added feature2 in development branch"
     1 file changed, 2 insertions(+), 3 deletions(-)

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
</pre>




- In version01.txt of development branch add below lines after “This is the bug fix in development branch” that you added in Day10 and reverted to this commit.
- Line2>> After bug fixing, this is the new feature with minor alteration”

  Commit this with message “ Added feature2.1 in development branch”
- Line3>> This is the advancement of previous feature

  Commit this with message “ Added feature2.2 in development branch”
- Line4>> Feature 2 is completed and ready for release

  Commit this with message “ Feature2 completed”

<pre>
    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ echo "this is the new feature with minor alteration" >> ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git commit -m "Added feature2.1 in development branch"
[dev 32fadb6] Added feature2.1 in development branch
 1 file changed, 1 insertion(+), 1 deletion(-)

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ echo " This is the advancement of previous feature" >> ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git commit -m " Added feature2.2 in development branch"
[dev f0725fa]  Added feature2.2 in development branch
 1 file changed, 1 insertion(+)

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ echo "Feature 2 is completed and ready for release" >> ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git commit -m "Feature2 completed"
[dev 5fe0e67] Feature2 completed
 1 file changed, 1 insertion(+)

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)

  </pre>

  
- All these commits messages should be reflected in Production branch too which will come out from Master branch (Hint: try rebase).
<pre>
User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (dev)
$ git checkout -b production
Switched to a new branch 'production'

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git rebase dev
Current branch production is up to date.

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git status
On branch production
nothing to commit, working tree clean

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git log
.
  .
  .
  ..
  
User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git push origin production
Enumerating objects: 24, done.
Counting objects: 100% (24/24), done.
Delta compression using up to 24 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (20/20), 1.45 KiB | 1.45 MiB/s, done.
Total 20 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
remote: This repository moved. Please use the new location:
remote:   https://github.com/kmahendra999/DevOps.git
remote:
remote: Create a pull request for 'production' on GitHub by visiting:
remote:      https://github.com/kmahendra999/DevOps/pull/new/production
remote:
To https://github.com/kmahendra999/Devops.git
 * [new branch]      production -> production

</pre>

# Task-03
- In Production branch Cherry pick Commit “Added feature2.2 in development branch” and added below lines in it:
<pre>
git log
git checkout production
git log
git cherry-pick f0725fa4bf8a73c70edaebb77b33034f8042bceb
git cherry-pick --continue
git cherry-pick --continue
git add .
git commit -m "testy"
git cherry-pick --continue
git commit --amend
git cherry-pick --continue
git push origin production
git log

  </pre>
- Line to be added after Line3>> This is the advancement of previous feature
- Line4>>Added few more changes to make it more optimized.
- Commit: Optimized the feature

<pre>
User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ echo "This is the advancement of previous feature" >> ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ echo "Added few more changes to make it more optimized." >> ./Devops/Git/version01.txt

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git add .
warning: in the working copy of 'Devops/Git/version01.txt', LF will be replaced by CRLF the next time Git touches it

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git commit -m "Optimized the feature"
[production 6d498de] Optimized the feature
 1 file changed, 2 insertions(+), 1 deletion(-)

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
$ git push origin production
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 24 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 497 bytes | 497.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
remote: This repository moved. Please use the new location:
remote:   https://github.com/kmahendra999/DevOps.git
To https://github.com/kmahendra999/Devops.git
   56f4327..6d498de  production -> production

User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (production)
</pre>

## Reference [video](https://youtu.be/apGV9Kg7ics)


You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)
