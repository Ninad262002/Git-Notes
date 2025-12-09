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





