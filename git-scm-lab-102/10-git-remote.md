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

### Adding remote repositories

To add a new remote Git repository as a shortname you can reference easily, run `git remote add <shortname> <url>`:

```git remote add origin https://github.com/aossama/simple-html-app```{{execute}}

## Protip
