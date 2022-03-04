# Git and GitHub (Part 1) 
<br>             

<div align="center">
<img style="float: block; margin: 0" width="400" height="200" src="git-image.png"> 
</div>

<br>

This article will provide an in-depth explanation of Git and its many useful commands, in an attempt to clarify much of the confusion on this subject matter. Admittedly, when I first started using Git and GitHub, I was perplexed, to say the least. After months of head scratching, trial, and absorbing knowledge from numerous resources, I finally understood the topic on a proficient level. However, for such a vital and widely used tool, there should be a more efficient way of teaching this material. Therefore, I am here to share some insight on what helped me to understand (and appreciate) Git on a functional level. 

<br>

### What is Git?
<br>

Before we dive into any subject matter, we first must ask ourselves two imperative questions - "What is it?" and "Why do I need to learn it?". 

Simply put, Git is a version control tool that manages file and code revisions. In other words, Git is a system that maintains a history of your code edits by tracking and storing changes you make to your code. Git has become the most commonly used and expected version control system in the industry. Therefore, it is just crucial to learn Git as it is to learn a programming language. Moreover, as a developer, it is imperative for you to be proficient with Git because Git provides:

- efficient project collaboration
- seamless code integration  
- centralized location to store your work
- isolated environment for code changes
- easy access to prior code content
- full local history stored on your machine
- error reversal
- file recovery
- ability to work offline
- and much more!

Now with that in mind, I want to clarify a few terminology that puzzled me early on, before we jump into the material.  

<br>

#### Is Git and GitHub the same?
<br>

Firstly, although the name may be misleading, Git is NOT short for GitHub. While Git is a version control tool, GitHub is an online platform that is used in conjunction with Git to store remote projects (also known as "repositories" or "repos"). There are other Git repository hosting services such as GitLab, BitBucket, CodeBase, etc; however, GitHub has become the largest community website for software development and the industry standard for hosting Git repositories, so that is the platform I will be discussing in this article. 

<br>

Secondly, many of Git's commands involves retreiving or releasing files between GitHub and your local machine. A "local" repository resides offline on a computer, whereas a "remote" repository resides online in GitHub. A repository may reside in either locations or both at any given time. One of Git's main functions includes synchronizing the two versions of your files (local and remote) which we will discuss in detail later on. 

<br>

### Getting Started
<br>

In order to begin, you need to:

- install [Git](https://git-scm.com/downloads),
- create a [GitHub](https://github.com/) account,
- open a code editor, and
- open a command line interface (often referred to as the command line or terminal) and be sure to understand the basic prompts.

<br>

### Setup and Configuration
<br>

After you have installed Git, provide a username and email (for Git to identify you as the author on future commands) by running the following commands:

```

$ git config --global user.name "Jane Doe"
$ git config --global user.email "jane_doe@company.com"

```

Security is of the utmost importance with Git and GitHub. Therefore, you need to generate an SSH key to authenticate and connect your local machine to GitHub. Fortunately, GitHub offers detailed documentation and assistance on [checking](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys) for an existing key, [generating](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) a new key, and [adding](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) the new key to GitHub. 

<br>

Now that you have completed these steps, you are *finally* ready to use Git and GitHub...phew!

<br>

### Git Init
<br>
  
From your terminal (assuming you have a basic understanding of the command line), navigate to a folder that contains files you wish to conduct version control with and upload to GitHub. Please note that, for organization purposes, each of your projects should reside in a separate folder. After navigating to said folder, initialize your project by running ```git init``` which will alert Git to listen for file changes in this folder. This command will create a .git (hidden) directory that stores the metadata and files with your saved code changes. If you wish to change the root directory of your Git repository, simply move this .git directory to the desired folder. If you want to undo the initialization of your project entirely, simply remove this .git directory. Please note that, removing the .git directory is irreversible and will discards any changes that are not in a remote repository. 

<br>

## Git Status and Git Add
<br>

After initializing your project, you will notice that changes you make to a file in that directory will be prompt an alert from Git. At this phasse in the workflow, if you run ```git status```, you will see a list of modified files under "Untracked files: " in red text. An untracked file indicates that Git has not yet been informed of the file's existence. 

<br>

<img style="block: left; margin: 0" width="400" height="100" src="git-untracked.png">

<br>

To utilize Git's version control system, you need to specifically instruct Git which files you want Git to track by using ```git add```. This command will send the specified file to the index (also referred to as the stage or staging area) which is a holding area for files that are ready to be saved or committed (I will discuss commits in the next section). The ```git add``` command may be used in the following manners:

- ```git add <filename>``` : adds specified file to index
- ```git add *.<extension>``` : adds all files with specified extension to index
- ``` git add .``` or ```git add -A``` : adds all files to index
- ```git add -u``` : adds only deleted and modifed files to index

<br>

<img style="block: left; margin: 0" width="400" height="100" src="git-staged.png">

<br>

Modified or new files that have been added to the staging area, are now considered tracked files and will appear in green text if you ran ```git status``` once more. In other words, Git will only perform version control on staged/tracked files. Please note that, if you make changes to staged files, you will need to re-add them to the index; otherwise, Git will not be aware of the subsequent changes. If you modified files that are already staged, and run ```git status``` those files will reappear in red text, which indicates there are additional file changes that have not been staged. 


<br>

You may also use ```git reset``` to remove files from the stage, if you decide you are not ready to stage your files. The ```git reset``` command may be used in the following manner:

- ```git reset <filename>``` : removes specified files from the index
- ```git reset``` : removes all files from the index

<br>

## Git Commit and Git Log
<br>

In Git, a commit is essentially a snapshot of file changes and represents a version of the entire repository at a particular time. 

<br>
