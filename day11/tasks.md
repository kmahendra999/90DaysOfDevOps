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

    User@PARAM MINGW64 /d/OneDrive/Desktop/90Days (desginer)
  </pre>

# Task-02
- In version01.txt of development branch add below lines after “This is the bug fix in development branch” that you added in Day10 and reverted to this commit.
- Line2>> After bug fixing, this is the new feature with minor alteration”

  Commit this with message “ Added feature2.1 in development branch”
- Line3>> This is the advancement of previous feature

  Commit this with message “ Added feature2.2 in development branch”
- Line4>> Feature 2 is completed and ready for release

  Commit this with message “ Feature2 completed”
- All these commits messages should be reflected in Production branch too which will come out from Master branch (Hint: try rebase).

# Task-03
- In Production branch Cherry pick Commit “Added feature2.2 in development branch” and added below lines in it:
- Line to be added after Line3>> This is the advancement of previous feature
- Line4>>Added few more changes to make it more optimized.
- Commit: Optimized the feature


## Reference [video](https://youtu.be/apGV9Kg7ics)


You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)
