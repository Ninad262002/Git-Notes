# Git-Notes
Git Notes for personal revision 

What is git?
Ans - Git is a content tracker and a open source distributed version control system. 

Git has two repositroy local and remote ?
Ans - local repository is one which is present in your computer
      Remote repository is usually a centralized server

Local repository has three section  - working area , staging area , commited area

git --help
git --init to initialize a repo
git status - to check the status of files under repo
git add file_name - it will move file from working area to staging area
git commit -m "this is my first commit" - to commit the changes


before commiting git should know who you are so to set that
git config user.name "sarah"
git config user.email "sarah@gmail.com"

git restore <file_name> = when you accidently change the files in working area you can restor it to previosus version using this command

git add . = this swill stage both of the files once

git rm <file_name> = The git rm <file_name> command is used to remove a file from both the Git repository (staging area) and the local working directory depending on options which you choose
(use --chahed to keep the file , or -f to force removal)

to perminently ignore a file put the name of that file in ".gitignore"
echo "notes.txt" > .gitignore


git log 
git log --name-only = to see files as well
git log -n 1 = to see latest commit 


:star: Git Branch
I usually explain a git branch as a parallel line of development that diverges from the main project at a specific point in time.
The primary purpose of branching is isolation and safety. It allows our team to work on new features or bug fixes in a contained environment without affecting the stable, production-ready code on the main branch.

    git branch sarah = Create a new branch
    git checkout sarah = switch to a branch 
    git checkout -b sarah = create a new branch and immediately switched to a new branch 'sarah'
    git branch = to see the list of branches
    git branch -d max = delete a branch


HEAD - it points to the last commit in your current branch. 


    git log --graph --decorate
--graph = it will show you git branches in graphical formate 
-- decorate = it will create a chart with * and |
<pre>
ex -
  *
  |
  |  *
  *  |
  |  * 
  | /
  *
</pre>
 Graph lines
    The | and * characters show how branches split:
    * → a commit
    | → the commit line
    Branches diverge when lines split
    This is Git’s simple visualization of commit history.

          git log --graph --decorate --oneline --all
This is the BEST command to see:
  All branches 
  Their commit history
  A visual graph

:star: Git Merge
Git has two type of merge "fast-forward" merge and "non-fast-forward" merge
git merge <branch_name>

:star: Initializing Remote Repository
Their are several platform on which we can host our remote repository like GitHub, GitLab, Bitbucket.

Connection string is an url which let git know where the remote repository is located.

We can add the remote repository to local repository with.
    git remote add origin <https://.../.../ connection string>

To list all remote git repositories.
    git remote -v

:star: Pushing 

In order to keep our local and remote repository in sync, we have to push the data from our local repository to the remote repository.

    git push origin master 

:star: Cloning
It allows a person to clone a remote repository in order to get all this data on their local machines.

     git clone [ ssh link ]

:star: Pull Request

A Pull Request (PR) is a request to merge your changes from one branch into another branch.
It’s mainly used when you want someone to review your code before it becomes part of the main project.

Simple Example
   Let’s say you have a project on GitHub with these branches:
        main
        feature-login
   You worked on the feature-login branch and finished your task.
   Now you want these changes added to the main branch.
   You will create a Pull Request.
 
Steps to Create a Pull Request (GitHub UI)
1. Push your branch to GitHub
2. Go to the repository page
3. GitHub will show: “Compare & pull request” — click it
4. Add a title and description about what you changed
5. Click Create pull request
6. Reviewer checks your code
7. Reviewer approves
8. Click Merge pull request


:star: Fetching and Pulling

Git Fetch
What is does:
Downloads the latest changes from the remote repository 
Does not change your working branch or current branch.

    git fetch origin
    #To check changes
    git log origin/master
    git diff main origin/master

 Git Pull
 What it does:
 Downloads changes AND immediately merges them into your current branch.
 
    git pull origin master

:star: Merge Conflicts
A merge conflicts happens in Git when it cannot automatically combine changes from two branches.

:star: Fork
A fork in GitHub is a personal copy of someone else's repository that lives in your GitHub account.

:star: Rebasing
 Rebase= Make your work on top of the latest changes.

  Situation
   You started working on a feature branch. Meamihile, new commits were added to main. 
   Your branch is now behind main,
  What rebase dose?
  Rebase take your commits, temporarily removes them, updates your branch with the latest main, and then puts your commits back on top.
  Result: clean, straight commit history (no extra merge commits) 
  
  Simple example

     git checkout feature
     git rebase main
  This means:
    1. Git pauses your feature commits 
    2. Updates your branch with main
    3. Re-applies your commits one by one.
    
:star: Interactive rebase

Interactive rebase lets you edit and clean up your commits before merging a branch.
If your feature branch has many small or messy commits, you can combine (squash) related commits into one clear commit.
This keeps the project history clean, readable, and meaningful.

How to start Interactive rebase

    git rebase -i HEAD~4
When you execute this command, Git displays a list of the selected commits along with the default command (usually "pick") and a set of instructions. The output may look like this:

      pick fb9f191 Added second story
      pick aaba5e7 Changes to second story
      pick 8ad5d7b Oops more changes to second story
      pick 6a6f68b More changes to second story
      # Rebase dc9ad3c..6a6f68b onto 6a6f68b (4 commands)
      #
      # Commands:
      # p, pick <commit> = use commit
      # r, reword <commit> = use commit, but edit the commit message
      # e, edit <commit> = use commit, but stop for amending
      # s, squash <commit> = use commit, but meld into previous commit
      # f, fixup <commit> = like "squash", but discard this commit's log message
      # x, exec <command> = execute command (the rest of the line) using shell
      # b, break = stop here (continue rebase later with 'git rebase --continue')
      # d, drop <commit> = remove commit
      # l, label <label> = label current HEAD with a name
      # r, reset <label> = reset HEAD to a label
      # m, merge [-C <commit> | -c <commit> | <label> [# <oneline>]]
      #   : <message> (or the oneline, if no original merge commit was
      #     specified). Use <commit> to reword the commit message.
During interactive rebase, change pick to squash for the commits you want to combine.
Save and exit, and Git will merge those commits into one single commit with all their changes.

:star: Cherry-Picking
Cherry-pick Take one specific commit from another branch and apply it to your current branch.
you don't merge the whole branch you pick only what you need

Simple example

:- main branch

:- feature branch with many commits

you only want one bug-fix commit from feature.

     git checkout main
     git cherry-pick <commit-id>

That single commit is copied and added

:star: Resetting and Reverting
If you make an unwanted commit, Git lets you undo it safely using revert or reset, depending on whether you want to keep or change commit history.

📌 Reverting a commit 
 Git revert is used to undo a commit without changing Git history.
 It creates a new commit that reverses the changes of a previous commit, which makes it safe to use on shared branches like main.

 $ git revert 8ad5d(commit id)  

 📌 Resetting a Commit
    git reset is used to undo commits.
    You can choose whether to keep the changes or delete them.
    🔹 Soft Reset 
        Removes the commit
        Keeps the changes staged
        Useful when you want to edit and recommit

        git reset --soft HEAD~1
 Result:
   Commit is removed
   File is still in staging area

   🔹 Hard Reset
        Removes the commit
        Deletes all changes
        File is completely removed
        
         git reset --hard HEAD~1
         
⚠️ Warning: Changes are permanently lost


| Command                   | What it does                                    |
| ------------------------- | ----------------------------------------------- |
| `git revert <commit>`     | Safely undoes a commit by creating a new commit |
| `git reset --soft HEAD~1` | Removes commit but keeps changes                |
| `git reset --hard HEAD~1` | Removes commit and deletes changes              |





 

 






 




 











