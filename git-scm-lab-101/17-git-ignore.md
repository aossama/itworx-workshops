Sometimes there are particular files or directories you never want to commit them into the repository, such as local development configuration files. To ignore these files you create a `.gitignore` file in the root of the repository.

The .gitignore file allows you to define wildcards for the files you wish to ignore, for example \*.tmp will ignore all files with the extension .tmp.

Any files matching a defined wildcard will not be displayed in a git status output and be ignored when attempting the git add command.

## Task

Add and commit a .gitignore file to the repository to ignore all \*.tmp files.

Add file called `file.tmp`{{open}} with some content.

<pre class="file" data-filename="./file.tmp" data-target="replace">
This is a tmp file.

The file will be ignored by git.
</pre>

Inspect the repository with ```git status```{{execute}}. It'll show the file as an untracked file. Now go ahead and create a `.gitignore`{{open}} file. And ignore all \*.tmp files:

<pre class="file" data-filename="./.gitignore" data-target="replace">
*.tmp
</pre>

Then inspect the repository again with ```git status```{{execute}}. You'll notice that `file.tmp` has been ignored from being tracked by git. Also since `.gitignore` is another file it'll need to be tracked.

So let's add the file to the repository and commit, use;

```git add .gitignore```{{execute}}

```git commit -m "Adding .gitignore"```{{execute}}

## Protip

* The .gitignore should be committed to the repository to ensure the rules apply across different machines.
