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

 






 




 











