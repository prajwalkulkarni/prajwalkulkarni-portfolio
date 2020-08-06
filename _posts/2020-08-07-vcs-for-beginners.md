---
layout: post
title: "VCS for beginners"
date:   2020-08-06
excerpt: "VCS and git commands for beginners"
image: "/images/vcs.png"
categories: coding
---

While you’re working on a project with your fellow teammates or working as an independent developer, it is important to have a structured roadmap and go as per the schedule, as it helps you achieve milestones and complete the work in a given timeframe. Completion of any work contains some common practices, such as understanding the requirement, dividing the task into several smaller tasks, starting with the easier ones, and finally getting an end result.
As you progress working on a project, there’s always a certainty that something might get screwed and ruin all your hard work. (Here, hard work didn’t really pay well :P) . Hence, it’s a good idea to save a copy after completing each task or at any stage, anything that comforts you.
So, in today’s article, we’ll look at, how you can track and maintain your code, for a better coding environment.<br>

<h2>What is VCS?</h2>
VCS stands for <b>“version control system”</b>, but what does version control system mean?<br>
<h3>A Stringent definition:</h3>
<i>In software engineering, version control is system responsible for managing changes to computer programs, documents, large web sites, or other collections of information.</i><br>
Putting it in simpler words, it’s a file management system used to track changes, undo to a previous stage, and much more.
Now, let us look at how to set up a VCS for your project and store it on a remote host.
We’ll be using git and Github to track and host files.
Often a times beginners are quite confused between git and Github, many assume that both are more or less the same.<br>
<h3>Difference between git and Github</h3>
As discussed above, Git is a version control system used to track and manage your source code history, and GitHub, as the name suggests is a hub to remotely host your files. As simple as that.
With that being clear, we shall look at a few very basic terminologies most widely used in the git context.
<ul>
<li>Repository: It is a place where your code(project) is hosted under a name, or may consider it as a root directory of your project, with the repository name being the name of the directory.</li>

<li>Branch: Branch is a sub-part in a working tree. A lightweight movable pointer pointing to the current branch(with the default branch being, the MASTER branch). It is mainly used to store different versions of files simultaneously without any conflicts. You can have multiple branches for a single repository.
</li>

<li>Commit: To commit is to update changes in the codebase, committing a file(s) means adding a checkpoint to the changes made.
</li>

<li>README.md: A markdown file used to give a piece of thorough information to the users of what’s the software/project all about, usage et cetera.</li>
</ul>
Now, that you’ve an idea of what git is, let’s get started.
Firstly, you’ll need to have Git installed on your machine.
You can download it from here.
We’ll be working on CLI over GUI in this article.
Files/directories need to be staged to track changes, so fire up your favorite terminal and navigate to your project directory and type:
```
git init
```
This will initialize your local repository, so that you can add the required files for tracking.
To stage the files, use the below command.
```
git add <file-or-dir-name>
git add *
```
The above commands are used to enable tracking to specified files, (*) implies all the files/dirs.
If you’d want to know the current file status,
```
git status
``` 
This will give you a brief information of the files which are actively being tracked, modified and also a list of untracked files, if you’d want to add any file for tracking, you could use the ‘git add’ command to do so.
Moving further, let us look at how to commit changes. Commits in git are like adding checkpoints.
When you commit a file, it means you’re setting up a reference point, where you could always go back.
You can either commit a single file or the whole repository at once.
When you commit a file(s), an alphanumeric string is generated, called as ‘commit-id’, if you ever want to revert back to a certain stage or look at the changes made, you could use this ‘id’ to extract details about a particular commit. This id can be obtained by using the command,
```
git log
git log --all
```
‘git log’ shows recent commits, the same command used with an argument ‘ — all’, shows the complete history of all the commits in a repo.
Now, that we’ve seen what ‘commits’ are and how to monitor them, it is time to get to know how to commit files.
While committing any file, it’s a good rule of thumb to provide a short description of what changes/addition are made. As it helps others and yourself to understand what’s going on.
Consider, you’re working on a website, and are currently working on a webpage, you just completed fixing styling issues and added footer.
You’re now ready to add a checkpoint(commit), you could add a commit-message like, “Fix styling and add footer”, and not something like “Time to party”. Note that, in the commit-message, I’ve used present tense instead of past tense, which otherwise would be “Fixed styling issues and added footer”.
Present tense is used to past tense, because:
<ul>
<li>It is more concise.</li>
<li>It tells someone what applying that commit will do, so it should read something like If I apply this commit, it will [make foo do something...]</li>
</ul>
The syntax to commit a file is as follows:
```
git commit <file-name> -m "Commit message"
git commit . -m "Commit message here"
```
If you use a period(.) instead of a file name, all the modified files will be committed under the same commit message in a working repository.
To go back to the previous commit/state:
```
git checkout <filename>
```
Up until this point, any changes, addition, modification, and tracking was localized on your machine. It’s always safe to have a backup elsewhere, an external storage would do, but definitely not advised when there’s GitHub.<br>
GitHub, Inc. is a United States-based global company that provides hosting for software development and version control using Git. It has been a subsidiary of Microsoft since 2018. It offers the distributed version control and source code management functionality of Git, plus its own features.
If you don’t have a Github account yet, create one right now.
Once you sign up, create a repository by clicking on the ‘New’ button, and fill the required fields. Make sure to keep the repository public for now.
Soon after creating a repository, you get some instructions on how to set up your project with the newly created repository. Copy the git URL, which looks something like this:
```
github.com/<username>/<repo-name>.git
```
Now head back to your terminal and navigate to your local repository, establish a pathway with a remote repository(the repo you just created on Github) by executing the following command:
git remote add origin github.com/<username>/<repo-name>.git
There’s one last step to host to your files on a remote repo, i.e, Github repo.
You can add files to your GitHub repo by pushing the committed files.
git push -u origin master
This pushes all the committed files to the master branch(default branch).
To list all the existing branches:
```
git -a branch
```
To create a new branch:
```
git checkout <branch-name>
```
So, this covers up all the basics to get you started and going with VCS.
You might as well need to know a few other terms.<br>
<b>Fork:</b> Creating a “fork” is producing a personal copy of someone else’s project. Forks act as a sort of bridge between the original repository and your copy of the same.<br>
<b>Star:</b> Some people use “stars” to indicate that they like a project, other people use them as bookmarks so they can follow what’s going on with the repo later.<br>
<b>Pull request:</b> Pull requests let you tell others about changes you’ve pushed to a GitHub repository.<br><br>

<h3>Wrapping Up</h3>
In this article, you were introduced to what is VCS, git and GitHub, some git commands to initialize, commit and push changes onto remote repo.
You can have a look at this cheat sheet, which includes some of the most commonly used git commands along with a brief description of the same. You can also add other missing commands from the list along with a simple explanation of what it does(Submit a pull request).
Feel free to give a “clap” if you found this helpful, you could connect with me on <a href ="https://in.linkedin.com/in/prajwal-kulkarni" target="_blank">LinkedIn</a> or/and <a href="https://www.instagram.com/prajwalkulkarni_" target="_blank">Instagram</a>.