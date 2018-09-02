`git merge` command lets you take the independent lines of development created by `git branch` and integrate 
them into a single branch. `git merge` will combine multiple sequences of commits into one unified history. 
In the most frequent use cases, `git merge` is used to combine two branches.

## Preparing to merge

Before performing a merge there are a couple of preparation steps to take to ensure the merge goes smoothly.

### Confirm the receiving branch

Execute `git status` to ensure that HEAD is pointing to the correct merge-receiving branch. If needed, execute 
`git checkout <receiving>` to switch to the receiving branch. In our case we will execute git checkout master.

Let's merge the branch called _my-feature_ into the _master_ branch. Checkout _master_ branch with ```git checkout 
master```{{execute}}.

### Fetch latest remote commits

Make sure the receiving branch and the merging branch are up-to-date with the latest remote changes. Execute 
`git fetch` to pull the latest remote commits. Once the fetch is completed ensure the master branch has the 
latest updates by executing git pull.

Now just to make sure that the master branch has the latest content from the upstream using;

```git fetch```{{execute}}

```git pull```{{execute}}

### Merging

Once the previously discussed "preparing to merge" steps have been taken a merge can be initiated by executing 
`git merge <branch name>` where <branch name> is the name of the branch that will be merged into the receiving branch.

The useful `--merged` and `--no-merged` options can filter this list to branches that you have or have not yet merged into the branch you’re currently on. To see which branches are already merged into the branch you’re on, you can run `git branch --merged`.

Let's merge the _my-feature_ branch into the _master_ branch. First inspect the unmerged branch, use;

```git branch --no-merged```{{execute}}

Which will show you all the unmerged branches. Then start merged the _my-feature_ branch, use;

```git merge my-feature```{{execute}}

Which will show you that git did a fast-forward merge;

<pre>
Updating 650ebde..94eb317
Fast-forward
 about.html | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 about.html
</pre>

At this point the local master branch is ahead of the remote master branch with one commit, use ```git push```{{execute}} 
to publish the local commits.

### Delete merged branch

After you've merged the branch, it's now safe to do some house keeping and delete the merged branch, use;

```git branch -d my-feature```{{execute}}

## Resolving conflict

If the two branches you're trying to merge both changed the same part of the same file, Git won't be able to figure out which version to use. When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually.

How conflicts are presented
When Git encounters a conflict during a merge, It will edit the content of the affected files with visual indicators that mark both sides of the conflicted content. These visual markers are: <<<<<<<, =======, and >>>>>>>. Its helpful to search a project for these indicators during a merge to find where conflicts need to be resolved.

<pre>
here is some content not affected by the conflict
<<<<<<< master
this is conflicted text from master
=======
this is conflicted text from feature branch
>>>>>>> feature-717
</pre>