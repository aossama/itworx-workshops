In Git terms, a "checkout" is the act of switching between different versions of a line of development. The `git checkout` 
command operates upon three distinct entities: files, commits, and branches. In addition to the definition of "checkout" 
the phrase "checking out" is commonly used to imply the act of executing the `git checkout` command.

The `git checkout` command lets you navigate between the branches created by `git branch`. Checking out a branch updates 
the files in the working directory to match the version stored in that branch, and it tells Git to record all new commits 
on that branch. Think of it as a way to select which line of development you're working on.

## Task

### Check out existing branch

```git checkout demo-feature```{{execute}}

### Create a new branch

`git checkout` works hand-in-hand with `git branch`. The `git branch` command can be used to create a new branch. When you 
want to start a new feature, you create a new branch off master using `git branch new_branch`. Once created you can then 
use `git checkout new_branch` to switch to that branch.

The `git checkout` command accepts a **-b** argument that acts as a convenience method which will create the new branch and 
immediately switch to it. You can work on multiple features in a single repository by switching between them with `git checkout`. Go 
ahead and checkout a new branch with;

```git checkout -b stable```{{execute}}

The above example simultaneously creates and checks out `yet-another-branch`. The -b option is a convenience flag that tells Git to run git branch <new-branch> before running git checkout <new-branch>.

```git checkout  -b unstable stable ```{{execute}}

By default `git checkout -b` will base the new-branch off the current **HEAD**. An optional additional branch parameter can be passed to git checkout. In the previous example, _stable_ is passed which then bases new-branch _unstable_ off of existing-branch instead of the current **HEAD**.

### Switching Branches

Switching branches is a straightforward operation. Executing the following will point HEAD to the tip of _stable_ branch.

```git checkout stable```{{execute}}

Git tracks a history of checkout operations in the reflog. You can execute git reflog to view the history.

### Checkout a Remote Branch

When collaborating with a team it is common to utilize remote repositories. These repositories may be hosted and shared or they may be another colleague's local copy. Each remote repository will contain its own set of branches. In order to checkout a remote branch you have to first fetch the contents of the branch.

```git fetch --all```{{execute}}

Uou can then checkout the remote branch like a local branch.

`git checkout <remotebranch>`
