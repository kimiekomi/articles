# Git and GitHub (Part 3) 
<br>             

<div align="center">
<img style="float: block; margin: 0" width="400" height="200" src="images/git-github-image.png"> 
</div>

<br>

This article will provide a detailed explanation of advanced Git and GitHub operations. In my previous Git and GitHub articles, I discussed the GitHub workflow and introduced - one of the most important Git features and concepts that aid in project collaboration - branching. The ability to create and navigate between branches allows developers to work independently and isolate their program endeavors from the main codebase. To provide individual testing of project features, branching works best when each branch represents a singular characteristic or entity of the main project. When development branches are completed, they are integrated back to the main branch. This stage of the workflow is where we left off in the last article on this topic. 

So without further adieu, let's immerse into the world of Git and GitHub!

<br>

### Git Merge and Git Rebase
<br>

To incorporate two different branches, use the ```git merge <branch name>``` command. Please note that, you must switch to the "receiving" branch then provide the "giving" branch's name (the branch with the code modifications) when running ```git merge <branch name>```. You may also combine the two commands into one command by running ```git merge <giving branch name> <receiving branch name>``` without having to checkout a branch beforehand. Both of the above commands will generate a new merge-commit in the development branch and Git will then seamlessly integrate the changes from one branch into the other. 

<br>

Another method to consolidate two branches, is through the ```git rebase <branch name>``` command (in this case, navigate to the *giving* branch then specify the *receiving* branch's name). This command will also integrate changes from one branch into the HEAD branch. However, instead of converging with the main branch at the HEAD, ```git rebase <branch name>``` will simply take all the commits in the development branch and append them to the HEAD. This method is less popular because it creates new commits for each prior commit in the main branch, thereby rewriting history in a sense. The main benefit to rebasing, is a cleaner or simpler project history. In other words, after rebasing, the git log will depict commits as one linear line, as if branching and reintegration did not occur.

<br>

<img style="float: inline; margin: 0" width="400" height="200" src="images/after-merge.png"> 
<img style="float: inline; margin: 0" width="400" height="200" src="images/after-rebase.png"> 

<br>

### GitHub Pull Request
<br>

hjkl

<br>