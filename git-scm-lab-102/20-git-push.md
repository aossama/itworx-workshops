The ```git push``` command is used to upload local repository content to a remote repository. Pushing is how you 
transfer commits from your local repository to a remote repo. It's the counterpart to ```git fetch```, but whereas 
fetching imports commits to local branches, pushing exports commits to remote branches. Remote branches are configured 
using the ```git remote``` command. Pushing has the potential to overwrite changes, caution should be taken when pushing.

## Task

When you have your project at a point that you want to share, you have to push it upstream. The command for this is 
simple: `git push <remote> <branch>`. If you want to push your master branch to your origin server (again, cloning 
generally sets up both of those names for you automatically), then you can run this to push any commits you’ve done 
back up to the server:

```git push origin master```{{execute}}

## Protip
