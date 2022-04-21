# Version Control in Git/Github for Gahlmann Lab

### A walkthrough of how to use Git/Github together

# Background

We will be doing all of our commands and pushes in the command line. There are GUI tools available but you will eventually run into a situation that you need the command line tools to do. 

First, a little background.

**Git** - Git is a version control software installed on your local machine

**Github** - Github is a for-profit company now owned by Microsoft. Github offers web based hosting for software and code repositories.

**Distributed Version Control** - Git is a distributed version control system. This means that there is not one master copy of the repository. Every developer who checks out the repository has a complete record of the project including all changes to the code. 

**Repository (repo)** - the basic unit in git. This is a record of all changes to specified files in your project.

**Fork** - personal copy of another user's repository

**Branch** - a parallel version of a repository. The top level branch of a repository is not called 'main', formerly called 'master'. 

# Setup

You must be set up with git/github before you are able to use them. 

### Mac/Linux users
Git comes with your operating system. No installation required.

### PC users
Need to install git and git bash. Watch the first 2:45 of this video: [https://www.youtube.com/watch?v=albr1o7Z1nw](https://www.youtube.com/watch?v=albr1o7Z1nw)

### Create GitHub account
Create a free account here: https://github.com/

# Scenario 1: Git Basics

Let's walk through a basic scenario where you have just installed git and github and are using it for the first time

#### Git configuration
Check your git version
```
git --version
```

Set up your config variables
```
git config --global user.name "Your name"
git config --global user.email "Your email"
```

### Clone existing Github repository
This is in the situation that you will be working from an existing Github repository. If you are just starting a new project, I recommend creating an empty repository first in Github.

```
git clone <url> <where to clone (optional)>

ex:
git clone https://github.com/epurpur/gahlmann-lab-version-control
```
This will clone (download) all files, code, change logs, etc for this project onto your project 

Navigate into the new directory
```
cd gahlmann-lab-version-control
```

View information about the remote repository. This can be useful especially in the situation that you have a local project you are working on and want to make sure it has been correctly connected to a github repository.
```
git remote -v
```

### Committing changes locally
Now that we have cloned a repository, we want to develop our code and make changes to it.

First, check the status of our repository
```
git status
```
We havent made any changes so the working tree should be clean. 

Now let's make some changes to the testcode.py file 

***to do this, open testcode.py in any text editor and make some changes to the code. It doesn't matter what changes are made***

Now, let's stage these commits **locally**. Let's see that these are being tracked by git now.
```
git status
```

Add these changes to the staging area

```
git add -A
```

Check the status again

```
git status
```

You see that these changes are ready to be committed

Now, let's commit these changes. Againk we are committing these changes **locally**

```
git commit -m "my message here"
```

Check status again to see that the working tree is clean

```
git status
```

### Committing changes remotely

Remember, the changes we have made are only in effect locally. Now we want to push these changes to our **remote** repository, which in this case is Github.

We are working on the main branch of this repository. We will cover branching in the next scenario.
```
git pull origin main

git push origin main
```

# Scenario 2: Branching

I briefly touched on branches earlier. Basically, branches are parallel versions of your codebase. The purpose of branching is so that multiple developers can work on code at the same time. This allows for faster development across your team. So far, we have been working only on the main branch of our repository. This isn't really how you should use version control and git in your daily workflow. 

A common workflow is to create a branch for your desired feature and then begin working off that branch. 

### Creating a branch

This creates the branch **locally**
```
git branch square_function
```

Now let's see our local branches to make sure it worked correctly. You see the * next to main, indicating we are still working in the main branch, though we have created a new one called 'square_function'.
```
git branch
```

Now we can move into our new branch. We must check out the branch in order to work in it.
```
git checkout square_function
```

Check to make sure you are working in the new branch

```
git branch
```

Now we can work on our new feature in this branch. Let's make some changes to our code. Once we have done that we will push hour changes to our **local branch**
```
git status

git add -A

git commit -m "added square function"
```

Push branch to **remote** repository. We have only made these changes locally so far.

```
git push -u origin square_function
```

The '-u' tells git we want to associate our local 'square_function' branch with our remote 'square_function' branch. 
Now, lets see the status of our branches both **locally** and **remotely**.

```
git branch -a
```

### Merging branches

Now that we have created a branch, pushed changes to it, and pushed it to our remote Github repository, it is time to merge our changes into the main branch, which is the top level branch in our repository.

We should check out our main branch **locally** first
```
git checkout main
```

Pull any changes that have been made to the main branch while we have been working on our new feature

```
git pull origin main
```

Merge our two branches **locally**
```
git merge square_function
```

### Deleting branches

It is good practice to delete branches once you have merged them with your main branch. This keeps them from cluttering your project

First, we will delete this branch **locally**
```
git branch -d square_function
```

Don't forget that this branch still exists in the remote repository
```
git branch -a
```

Let's delete this branch **remotely**
```
git push origin --delete square_function
```

# Best Practices






# Other Resources

Here are a few handy resources to refer to about what we have just covered

## Corey Schafer - git workflow series
Corey Schafer is a guy with a youtube channel that has made great videos that are very educational and easy to follow. I have based entirely what I covered on his version control workshops.
- [Git Basics](https://www.youtube.com/watch?v=HVsySz-h9r4)
- [Fixing Common Mistakes and Bad Commits](https://www.youtube.com/watch?v=FdZecVxzJbk&list=PL-osiE80TeTuRUfjRe54Eea17-YfnOOAx&index=2)
- [The rest of his git series](https://www.youtube.com/watch?v=FdZecVxzJbk&list=PL-osiE80TeTuRUfjRe54Eea17-YfnOOAx&index=2)

## Version Control best practices
- [My best practices cheat sheet](https://homes.cs.washington.edu/~mernst/advice/version-control.html)
