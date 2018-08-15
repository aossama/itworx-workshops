To save, or commit, files into your Git repository you first need to add them to the staging area. Git has three areas, a working directory, a staging area and the repository itself. Users move, otherwise referred to as promote, changes from the working directory, to a staging area before committing them into the repository.

One of the key approaches with Git is that commits are focused, small and frequent. The staging area helps to maintain this workflow by allowing you to only promote certain files at a time instead of all the changes in your working directory.

## Task
Use the command ```git add <file|directory>``` to add files or directories to the staging area after creating or modifying them.

```git add README.md index.html```{{execute}}

The primary function of the git add command, is to promote pending changes in the working directory, to the git staging area. If you make an additional change after adding a file to the staging area then the change will not be reflected until you add the file again.

Examine the result of this action by using the ```git status``` command;

```git status```{{execute}}

```touch file1 file2```{{execute}}

```git add file1```{{execute}}

## Protip

* The ```git status```{{execute}} command allows you to view the state of both the working directory and staging area at any point in time.

* To add all the files and directories from the working directory to the staging area run ```git add -A .```{{execute}}
