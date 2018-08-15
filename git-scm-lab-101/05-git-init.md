A Git repository is a virtual storage of your project. It allows you to save versions of your code, which you can access when needed. To store a directory under version control you need to create a repository. With Git you initialise a repository in the top-level directory for a project.

To create a new repo, you'll use the ```git init``` command. ```git init``` is a one-time command you use during the initial setup of a new repo. Executing this command will create a new .git subdirectory in your current working directory. This will also create a new master branch.

When a directory is part of a repository it is called a Working Directory. A working directory contains the latest downloaded version from the repository together with any changes that have yet to be committed. As you're working on a project, all changes are made in this working directory.

## Task

### Initializing a new repository

A sample projest has been populated in the current directory called project-1/. As this is a new project, a new repository needs to be created. Use;

```git init```{{execute}}

This command creates an empty Git repository - basically a directory called .git with subdirectories for objects, refs/heads, refs/tags, and template files. An initial HEAD file that references the HEAD of the master branch is also created.

### Inspect the repository

You can view which files have changed between your working directory and what's been previously committed to the repository using the command:

```git status```{{execute}}

The output of this command is called the "working tree status".

To view the raw directory of the newly created repository, use;

```ls .git/```{{execute}}

This will reveal all the files and directory which construct the repository.

## ProTip

* Running ```git init``` in an existing repository is safe. It will not overwrite things that are already there. The primary reason for rerunning git init is to pick up newly added templates.
* All files are "untracked" by Git until it's been told otherwise. The details of how is covered in the next step.