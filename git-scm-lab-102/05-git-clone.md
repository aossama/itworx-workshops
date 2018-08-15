If a project has already been set up in a central repository, the ```git clone``` command is the most common way for 
users to obtain a development copy. Like ```git init```, cloning is generally a one-time operation. Once a developer 
has obtained a working copy, all version control operations and collaborations are managed through their local repository.

The ```git clone``` clones a repository into a newly created directory, creates remote-tracking branches for each 
branch in the cloned repository (visible using ```git branch -r```), and creates and checks out an initial branch that 
is forked from the cloned repository's currently active branch.

## Task

Use the command ```git clone <repo>``` to clone a repository into a newly created directory. For example;

```git clone https://github.com/aossama/simple-html-app.git```{{execute}}

will create a new directory called `simple-html-app` from the upstream repository 
`https://github.com/aossama/simple-html-app.git`

As a convenience, cloning repositories automatically creates a remote connection called "origin" pointing back to the 
original repository. This makes it very easy to interact with a central repository. This automatic connection is 
established by creating Git refs to the remote branch heads under `refs/remotes/origin` and by initializing 
`remote.origin.url` and `remote.origin.fetch` configuration variables.

## Protip

* To clone the repository located at `<repo>` into the folder called `<directory>` using the command ```git clone <repo> <directory>```.
