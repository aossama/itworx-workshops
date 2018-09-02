`git checkout`  &#9733;  `git branch`  &#9733;  `git tag`  &#9733;  `git merge`  &#9733;  `git rebase`  &#9733;  `git reset`

This lab is a review of the `git branch` command and a discussion of the overall Git branching model. Branching is a feature available in most modern version control systems. Branching in other VCS's can be an expensive operation in both time and disk space. In Git, branches are a part of your everyday development process.

The implementation behind Git branches is much more lightweight than other version control system models. Instead of copying files from directory to directory, Git stores a branch as a reference to a commit. In this sense, a branch represents the tip of a series of commits—it's not a container for commits. The history for a branch is extrapolated through the commit relationships.

Throughout this lab you'll learn how to use;

* Switch between branches
* List, create and delete branchs
* Join branches together with merge
* Undo-ing changes using reset
