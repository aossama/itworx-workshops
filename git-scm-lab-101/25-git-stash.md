`git stash` temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. Stashing is handy if you need to quickly switch context and work on something else, but you're mid-way through a code change and aren't quite ready to commit.

## Task

### Stashing content

Let's introduct some changes to the working directory. Create a new file called `style.css`{{open}} and add some content to this file.

<pre class="file" data-filename="./style.css" data-target="replace">
html, body {
	margin:0; padding:0; background-color:#999;
}
</pre>

Then inspect the repository with ```git status```{{execute}}. This will show that a new untracked file has been added to the working tree.

Now let's use the `git stash` command which takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy. First let's examine if we have any stashed content or not;

```git stash list```{{execute}}

Which doesn't return anything because we do not have any stashed items. Now add the working tree as a stash with a message to identify this stash;

```git stash save --include-untracked "Stashing the stylesheet"```{{execute}}

Inspecting the working tree with ```git status```{{execute}} will reveal that all changes have been stored away. At this point you're free to make changes, create new commits, switch branches, and perform any other Git operations; then come back and re-apply your stash when you're ready.

### View stashed content

Use ```git stash list```{{execute}} to list the stashes that you currently have. Each stash is listed with its name (e.g.  stash@{0} is the latest stash, stash@{1} is the one before, etc.), the name of the branch that was current when the stash was made, and a short description of the commit the stash was based on.

<pre>stash@{0}: On master: Stashing the stylesheet</pre>

### Re-applying stashed content

Popping your stash removes the changes from your stash and reapplies them to your working copy. You can reapply previously stashed changes with ```git stash pop```{{execute}}.

### Commiting changes

Now add and commit the changes with;

```git add style.css```{{execute}}

```git commit --all --message="Add stylesheet style.css"```{{execute}}

## Protip

* Note that the stash is local to your Git repository; stashes are not transferred to the server when you push.