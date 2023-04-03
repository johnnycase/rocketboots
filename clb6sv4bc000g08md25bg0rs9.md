---
title: "A Git Primer for Beginners"
datePublished: Fri Dec 02 2022 17:48:49 GMT+0000 (Coordinated Universal Time)
cuid: clb6sv4bc000g08md25bg0rs9
slug: a-git-primer-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/0e5f1f01227de8ecca5613c5f442fa66.jpeg
tags: github, git, gitcommands

---

This short guide is intended to flatten the git learning curve for a beginner. The guide will cover the basics of getting started with git on the command line.

### Cloning a Repository
Cloning a repository is the git term for downloading a remote project to your local machine. You can do this with git clone repourl, just replace “repourl” with the url of the repository you want to clone. Doing this on a fork of the original repository is a good idea so you are not trying to commit changes directly to the main branch. Once the command completes, the project files will exist in your local folder. The git metadata, which is how git keeps track of changes, is hidden in the .git folder. To see the metadata files, show hidden files in your git repository folder.

### Making Changes
Once you have a current copy of the repository on you local machine, you are ready to begin making changes. After you make changes to a file, make a record of it with git add filepath, and replace “filepath” with the path to the changed file. Repeat git add until you have a record of all the changed files. Then run git status and make sure all the changed files show up.

### Commit Changes
Once your changes are done, it’s time to commit. I know what you’re thinking, but backing out of commits in git is painless! So don’t worry if you commit by mistake. In git, a commit is the record of changes you want to add to the online repository, a line in the sand if you will, that says, I own these changes. If you desire, you can make a commit for each file change; this gives you the option to back out a single change if needed. But if you are brave, you can commit all your changes in one go! The git commit -m "Commit Message" will commit the changes, then the only thing left is to push them to the online repository.

### Pushing Changes
After committing all your changes, they are ready to be pushed to the online repository. The git push repo branch will achieve this, but note that you will need to change repo and branch to the applicable repository and branch for your setup. If you are working from a fork that you cloned, using “origin” as your repo will likely work. This will push the changes to the repository defined as origin in your git metadata. If you are pushing to a branch of this repository, enter this after repo, but if you are not branching, enter main to push to the main branch. If you are in doubt, open your github repository in the browser and look at the different branches. If no branches exist, just push to the main branch.

This guide demonstrated how to use command line git to clone a repository, add changes, commit changes, and push to an online repository. Learning git can be daunting, but don’t give up! This guide is a great starting point and should encourage you to keep expanding your knowledge.