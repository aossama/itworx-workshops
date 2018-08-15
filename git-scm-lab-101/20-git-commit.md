Once a file has been added to the staging area it needs to be committed to the repository. The command ```git commit -m "commit message"``` moves files from staging to the repository and records the time/date, author and a commit message that can be used to add additional context and reasoning to the changes such as a bug report number.

Only changes added to the staging area will be committed, any files in the working directory that have not been staged will not be included.

## Task

### Save changes to the repository

To commit the staged file use;

```git commit -m "Initial commit"```{{execute}}

Examine the result of this action by using the ```git status``` command;

```git status```{{execute}}

## Protip

* Each commit is assigned a SHA-1 hash which enables you to refer back to the commit in other commands.

* To add the modified files to staging area and commit them on one step use the option -a with git commit command.
