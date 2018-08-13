Sometimes there are particular files or directories you never want to commit, such as local development configuration. To ignore these files you create a .gitignore file in the root of the repository.

The .gitignore file allows you to define wildcards for the files you wish to ignore, for example *.tmp will ignore all files with the extension .tmp.

Any files matching a defined wildcard will not be displayed in a git status output and be ignored when attempting the git add command.

## Task

Add and commit a .gitignore file to the repository to ignore all *.tmp files.

## Protip

The .gitignore should be committed to the repository to ensure the rules apply across different machines.
