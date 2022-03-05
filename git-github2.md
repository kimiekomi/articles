# Git and GitHub (Part 2) 
<br>             

<div align="center">
<img style="float: block; margin: 0" width="400" height="200" src="github-image.jpeg"> 
</div>

<br>

This article will provide further explanation of Git, GitHub, and their many useful (albeit often befuddling) operations. In my previous article on this subject matter, I briefly introduced GitHub - an online Git repository hosting service with the world's largest developer community. Much of the material I reviewed so far, merely pertained to local repositories. However, if you wish to collaborate with other programmers, share your work with the coding community, or store your repository online, then there are more advanced Git concepts and commands that you can employ.

So let's jump right in and pick things up where we left off!

<br>

### Git Push
<br>

Let's say, at the end of your workday, after you have commited your work to a local repository, you want to store your project on GitHub. At this point, you need to create a new empty repository on GitHub.com via the green "new" button on the upper left corner or the "+" button on the upper right corner of your GitHub homepage (as depicted in the image below by red circles).

<br>

<img style="float: block; margin: 0" width="600" height="200" src="new-repo.png"> 

<br>

Enter a name for your new repository, select the green "Create repository" button at the bottom of the page, then you will see your new repository's starter page. This page contains instructions on uploading your local project to GitHub. At the moment, all your work is only stored locally; therefore, you need to direct Git which remote repository you want your local project in. This step is accomplished with the ```git remote add origin <SSH URL>``` command (shown below with a red arrow). 

<br>

<img style="float: block; margin: 0" width="600" height="300" src="repo-home.png"> 

<br>

Afterwards, simply use the ```git push``` command to upload (also known as "push") your entire local repository to your newly created GitHub repository. Many developers choose to use the ```git push -u origin main``` command with the initial push. The ```-u``` flag is used to establish a tracking connection (or "upstream") between a local repository and the main "branch" (I will discuss branches in a later section). Establishing an upstream simply allows users to bypass typing "origin main" with each subsequent push. 

<br>

> Please Note: At the initial repositiory creation, one single branch is created. Git names this single branch "master". However, due to the negative connotations around the word "master", GitHub renames this initial branch to "main". That is why on the new repository starter page, GitHub includes instructions for renaming the initial branch (shown in the image above with a red asterisk). This is an optional step and can be done at any point in workflow. If you wish to observe modern conventions and industry standards, use the ```git branch -M main``` command to change the initial branch's name from "master" to "main". 

<br>

And just like that, your local repository is now online, meaning you have a remote version of your latest commit. At this stage, if you navigate to your repository starter page, you will see that the instructions have been replaced with a list of your files. 

Please note that, the repository starter page also provides instructions on creating a new remote repository from the command line. In other words, there is a *third* method to create a remote repository, aside from accessing GitHub.com. After commiting your code to a local repository, you can simply run ```git remote add origin <SSH URL>``` and push your project straight away, without visiting GitHub.com. However, instead of memorizing the SSH URL format, I choose to simply create a new remote repository through GitHub.com and copy/paste the URL from the starter page. 