# Global .gitignore

## Problem

Working on a project you may find that your favorite IDE wants to store project configuration files in a directory like `.idea` or `.vscode`. 
Normally you don't want to commit these files into a git repository, so we need to exclude them.

## Solution

One option could be to update project's `.gitignore` file with this directory name. But what if we have many repositories? In this case it would be better to have a global `.gitignore` that will be applied to all repositories. 

Create `.gitignore` in your HOME directory and put the required directories there. For example:

```
vim ~/.gitignore

.DS_Store
.idea
.vscode
```

Then we need to register this file in our global git configuration:

```
git config --global core.excludesfile ~/.gitignore
```
