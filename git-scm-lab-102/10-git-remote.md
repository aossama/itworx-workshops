The `git remote` command lets you create, view, and delete connections to other repositories. Remote connections 
are more like bookmarks rather than direct links into other repositories. Instead of providing real-time access to 
another repository, they serve as convenient names that can be used to reference a not-so-convenient URL.

## Task

### Showing remote repositories

To see which remote servers you have configured, you can run the git remote command. It lists the shortnames of each 
remote handle you’ve specified. If you’ve cloned your repository, you should at least see origin — that is the default 
name Git gives to the server you cloned from:

```git remote```{{execute}}

You can also specify -v, which shows you the URLs that Git has stored for the shortname to be used when reading and writing to that remote:

```git remote -v```{{execute}}

### Create a new GitLab project

In order to track the current repository which we cloned in a new repository, we need to create a project for it on the GitLab server.

1. In your dashboard, click the green **New project** button or use the plus icon in the upper right corner of the navigation bar.
2. This opens the **New project** page.
3. Provide the following information:

   * Project name: simple-html-app
   * Project description: Yet another simple HTML application
   * Visibility Level: Public

4. Click **Create project**.

### Manage remote repositories

Now let's manage this repository by replacing the remote one which was originally cloned to reference another remote repository that you've just created.

To rename a remote repository, use `git remote rename <old> <new>`, we'll rename the current one and make it point to out own repository on GitLab server.

```git remote rename origin old-origin```{{execute}}

To add a new remote Git repository as a shortname you can reference easily, use `git remote add <shortname> <url>`.

```git remote add origin https://github.com/aossama/simple-html-app```{{execute}}
