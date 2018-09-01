The `git pull` command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows.

The git pull command is actually a combination of two other commands, git fetch followed by git merge. In the first stage of operation git pull will execute a git fetch scoped to the local branch that HEAD is pointed at. Once the content is downloaded, git pull will enter a merge workflow. A new merge commit will be-created and HEAD updated to point at the new commit.

## How it works

The `git pull` command first runs `git fetch` which downloads content from the specified remote repository. Then a `git merge` is executed to merge the remote content refs and heads into a new local merge commit. To better demonstrate the pull and merging process let us consider the following example. Assume we have a repository with a master branch and a remote origin.

## Task

### Introduct some changes remotely

1. Navigate to your upstream repository on GitLab server http://git.itworx.cloud/<username>/simple-html-app.git
2. Add new **CHANGELOG** file by clicking on the **Add Changelog** button. This will open a text editor for entering the changelog context.
3. Go ahead and some content to the **CHANGELOG** file
4. Push the **Commit changes** button.

This will introduct some new changes on your remote repository that are not yet tracked by your local repository.

### Pull the updates

To get latest refs and content from your remote projects, use;

```git pull origin```{{execute}}

This will fetch the remote changes and merge them with the local branch and update the content of the working tree. The output will look like;

<pre>
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0)
Unpacking objects: 100% (3/3), done.
From http://git.itworx.cloud/aossama/simple-html-app
   1459192..90f500b  master     -> origin/master
Updating 1459192..90f500b
Fast-forward
 CHANGELOG | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 CHANGELOG
</pre>

Now inspect the local working directory using ```ls```{{execute}}, and you'll notice the newly created **CHANELOG** file has been applied to the tree.