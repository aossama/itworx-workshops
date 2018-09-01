`git clone`  &#9733;  `git remote`  &#9733;  `git fetch`  &#9733;  `git push`  &#9733;  `git pull`

Git's distributed collaboration model gives every developer their own copy of the repository, complete with its own 
local history and branch structure. Users typically need to share a series of commits rather than a single changeset. 
Instead of committing a changeset from a working copy to the central repository, Git lets you share entire branches 
between repositories.

The `git remote` command is one piece of the broader system which is responsible for syncing changes. Records 
registered through the git remote command are used in conjunction with the `git fetch`, `git push`, and 
`git pull` commands. The high level points this lab will cover are:

* Cloning remote repository
* Configuring remote repository
* Fetch from and integrate with another repository
* Update remote refs along with associated objects

By the end of this lab, you should be able to create a Git repo, use common Git commands to interact with remote 
repositories and share your work with others. This Scrapbook environment has been pre-configured with git installed. 
For more information on installing Git, please refer to the official documentation.