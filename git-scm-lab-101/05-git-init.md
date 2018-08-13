To store a directory under version control you need to create a repository. With Git you initialise a repository in the top-level directory for a project.

When a directory is part of a repository it is called a Working Directory. A working directory contains the latest downloaded version from the repository together with any changes that have yet to be committed. As you're working on a project, all changes are made in this working directory.

## Task

As this is a new project, a new repository needs to be created. Use

```git init```{{execute}}

This command creates an empty Git repository - basically a directory called .git with subdirectories for objects, refs/heads, refs/tags, and template files. An initial HEAD file that references the HEAD of the master branch is also created.

You can view which files have changed between your working directory and what's been previously committed to the repository using the command:

```git status```{{execute}}

The output of this command is called the "working tree status".

## ProTip

* Running ```git init``` in an existing repository is safe. It will not overwrite things that are already there. The primary reason for rerunning git init is to pick up newly added templates.
* All files are "untracked" by Git until it's been told otherwise. The details of how is covered in the next step.