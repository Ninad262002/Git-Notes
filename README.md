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


HEAD - it points to the last commit in your current branch 


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









