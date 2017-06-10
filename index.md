# Prerequisites
## Basic commands for Terminal/Command-line
Using the terminal type the different commands to do the different actions.

- Changing a folder
``` 
cd ..
```
- Listing your current location
```
pwd
```
- Making a folder 
```
mkdir folder_name
```
- Creating a file
```
touch filename.txt
```
- Listing folder contents 
```
ls -la 
```

Special folders that can be used in commands (e.g. `cd ..`)

- the root of your system `/`
- your user’s home `~`
- current directory `.`
- parent directory `..` 
 
You will not use more than these commands and concepts in this guide, but if you want to learn more try: 

- [Code Academy](https://www.codecademy.com/learn/learn-the-command-line) 
- [Appendix from - Learn Python the Hard Way](https://learnpythonthehardway.org/book/appendixa.html) 
- [Appendix from - Git Tower Tutorial](https://www.git-tower.com/learn/git/ebook/en/command-line/appendix/command-line-101) 

## Vi/Vim Basics
Vi is a command-line text editor 

To start editing a file with vi you type in the terminal
``` 
vi filename.txt
```

Vi has two modes: 

- **Command mode** Where letters are commands
- **Insert mode** Where you can type text

By default you are in **Command mode**. To be able to edit, type `i` to enter the **Insert mode**. You will notoice it will say **--Insert--** on the bottom of the screen.
To switch mack to **Command mode** press `Esc`.

To exit vi type one of the flowing: 

- `:wq` (save and quit)
- `:q!`  (simply quit without saving)
 
You will not really use this much, but it is good to know, in the rare case you do end up in vi.


# What is Git
Git is a free and open source version control system (https://git-scm.com/). 
 
Git looks scarier than it really is. Once you learn some of the commands, it just a matter of practicing. Harder to get the courage to get started, easier to use when it becomes a habit.

What is git used for
- Great for backups
- A tool to keep track of checkpoints in code or text

# Getting started
Git is literally a folder that you initialise to be tracked. For that I recommend the command line tool.

## Installing Git
Git has very good installation guide - [Git Downloads](https://git-scm.com/downloads) 
 
For advanced mac users I recommend (brew)[https://brew.sh/]. Install brew and then run in the terminal: 
```
brew install git 
```
 
## Initialising a repository (repo)
You start tracking a folder with git when you run the following command in that folder in the terminal:
```
git init
```

Once the folder has been initialized it is called a “git repository”. 
 
You can notice also that in the folder there will be a “.git” folder. This is used by git to keep track of the different states.

## Checking the repo status
To check the current status of a repository one can type in the terminal:
```
git status 
```
This will show you the state of different files (untracked, modified, deleted, ..) and also will give hints on what you could do next.
 
!!! I recommend to regularly check the status before running commands. 

## Changing something
One can create a file using this command:
```
touch README.md 
```
Then you can see the status of the repository:
```
git status
```
You can also see the difference to the past version:
```
git diff
```
If you add text you can see the lines that have been added. Try it out by adding some lines of text and then running the commands again.

## States of a change
A change can be a file added, a file changed but also several files changed in small ways.
 
A change goes through this states:

- **Untracked** - you’ve made a change and haven’t done anything
- **Staged for commit** - added locally but not finalised yet
- **Local repository** - Committed to the local repository 
- **Remote repository** - Committed to the remote repository in the cloud
 
We will cover the states throughout the guide.

## Committing a change 
In git when you add a change you run the following commands in the terminal
 
Add the change from being untracked to being staged for commit
```
git add .   
```
 
Commit your change to the local repository (the directory in your computer)
```
git commit -m “Your message” 
```
If you forgot to put `-m “Your message”` you will enter vi to add a message. Just follow the same steps as in the prerequisites and you will be fine. 

# Exercise 1
Take a project you had before and start using git on the side. 

Initialise the folder where the project is. Make sure there are no other things in that folder but your project, even if it is just a file. 
 
Make some changes to your project and commit them along the way following the commands described above. 
 
# Learning more

## Seeing the repo history
To list the changes you have committed you can run
```
git log 
```
Example output: 
```
~/git/kittens [master] $ git log
commit 4adab267027300b4d25eb3ff7fff66a54ea3bd3c
Author: Mariana B <mariana.b@example.com>
Date:   Fri Jun 9 19:39:32 2017 +0200
 
    Added description.
 
commit 189363237fcb733c88c4ba183777c39fea1d832f
Author: Mariana B <mariana.b@example.com>
Date:   Fri Jun 9 19:32:25 2017 +0200
 
    Initial commit
```
 
The long string with letters and numbers are commit hash codes. 
 
To compare two commits  together one can provide the hash codes to the diff command 
```
git diff 189363237fcb733c88c4ba183777c39fea1d832f 4adab267027300b4d25eb3ff7fff66a54ea3bd3c 
```
 
Also if you just provide one, it will compare to the current version you have.
```
git diff 189363237fcb733c88c4ba183777c39fea1d832f
```

Getting rid of changes
If your changes are added with `git add` you should run:
```
git stash 
```

Or run:
```
git reset HEAD  - 
git checkout -- .
```
 
Otherwise if it is not added yet just run
```
git checkout -- .
```
 
And then when you type `git status` you should get a message that nothing has changed since the last commit.

# Exercise 2
Try to see if you can revert changes in your repository. Delete lines and try to get them back through git. 
 
Do not forget to use `git status` and `git diff` it helps a lot with seeing what is your current state
 
# Remote repositories
Remote repositories are the ones that do not live locally on your computer but rather in the cloud. The main reasons one would do that is to share/collaborate on code and/or to back up the code in case their machine dies.

## Git repository hosting service providers

Some of the most known providers of such spaces are:   

- https://github.com/ - popular with open source communities
- https://about.gitlab.com/gitlab-com/ - provides private repositories for free
- https://bitbucket.org/ - team repositories 

## Why?
It is generally nice to build up a gitHub account with code so you can show what you have learned and worked with if you want to build a career in software development, especially if you do not have formal studies.

## Putting stuff in GitHub
For GitHub, just follow their instructions here:
https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/ 
 
Basically, if you have a local repo already, you should run for example:
```
git remote add origin https://github.com/nicevo/kittens.git
git push -u origin master
```

Next time you would need to push to remote you just need to run:
```
git push 
```

# Exercise 3
In the `README.md` add more text according to: 
[Markdown-Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
 
Then get the changes on GitHub
 
# Online classes
Different people learn differently, here are some online tutorial that can get you started:
 
- [Code Academy - Learn git](https://www.codecademy.com/learn/learn-git)
- [GitHub - Try git](https://try.github.io/levels/1/challenges/1)
- [Git Tower - Git tutorial](https://www.git-tower.com/learn/git/ebook/en/command-line/introduction) 
