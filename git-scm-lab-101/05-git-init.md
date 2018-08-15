A Git repository is a virtual storage of your project. It allows you to save versions of your code, which you can access when needed. To store a directory under version control you need to create a repository. With Git you initialise a repository in the top-level directory for a project.

To create a new repo, you'll use the ```git init``` command. ```git init``` is a one-time command you use during the initial setup of a new repo. Executing this command will create a new .git subdirectory in your current working directory. This will also create a new master branch.

When a directory is part of a repository it is called a Working Directory. A working directory contains the latest downloaded version from the repository together with any changes that have yet to be committed. As you're working on a project, all changes are made in this working directory.

## Task

### Populate a new project

We'll start off with just creating a simple project. Go ahead and create a README.md{{open}} file. And add some content to the README.md

<pre class="file" data-filename="./README.md" data-target="replace">
# Simple HTML Project

This is my first simple HTML project tracked by git.
</pre>

Then another file called index.html{{open}} with simple HTML content.

<pre class="file" data-filename="./index.html" data-target="replace">
<!DOCTYPE html>

<html>
  <head>
  	<title>Page title</title>
  </head>

  <body>
    <h1>My First Heading</h1>
    <p>My first paragraph.</p>
  </body>
</html>
</pre>

These two files will form the initial release of our small project.

### Initializing a new repository / git init

As this is a new project, a new repository needs to be created. Use;

```git init```{{execute}}

This command creates an empty Git repository - basically a directory called .git with subdirectories for objects, refs/heads, refs/tags, and template files. An initial HEAD file that references the HEAD of the master branch is also created. You will now have a .git directory, and you can inspect that with

```ls .git/```{{execute}}

This will reveal all the files and directory which construct the repository. For your new empty project, it should show you three entries, among other things:

* a text file called `HEAD`, that has `ref: refs/heads/master` in it. This is similar to a symbolic link and points at refs/heads/master relative to the HEAD file.
* a subdirectory called objects, which will contain all the objects of your project. You should never have any real reason to look at the objects directly, but you might want to know that these objects are what contains all the real data in your repository.
* a subdirectory called refs, which contains references to objects.

### Inspect the repository / git status

You can view which files have changed between your working directory and what's been previously committed to the repository using the command:

```git status```{{execute}}

The output of this command is called the "working tree status".

## ProTip

* Running ```git init``` in an existing repository is safe. It will not overwrite things that are already there.
* All files are "untracked" by Git until it's been told otherwise. The details of how is covered in the next step.