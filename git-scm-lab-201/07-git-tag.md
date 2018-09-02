Tags are ref's that point to specific points in Git history. Tagging is generally used to capture a point in history 
that is used for a marked version release (i.e. v1.0.1). A tag is like a branch that doesn’t change.

Unlike branches, tags, after being created, have no further history of commits. This lab will cover the different 
kind of tags, how to create tags, listing all tags, deleting tags, sharing tags, and more.

Git supports two types of tags: _annotated_ and _lightweight_.

## Annotated Tags

**Annotated tags** are stored as full objects in the Git database. To reiterate, they store extra meta data such as: the tagger name, email, and date. Similar to commits and commit messages Annotated tags have a tagging message.

## Lightweight Tags

**Lightweight tags** are very much like a branch that doesn't change — it's just a pointer to a specific commit.

## Task

### Creating a Tag

In order to create a new annotated tag identified with v1.4, use;

```git tag -a v1.4 -m "my version 1.4"```{{execute}}

Which will create a new annotated tag with the commit message specified by **-m** option. This is a convenience method similar to git commit -m that will immediately create a new tag and forgo opening the local text editor in favor of saving the message passed in with the -m option.

To create a lightweight tag identified as v1.4-lw. Lightweight tags are created with the absence of the -a, -s, or -m options. Lightweight tags create a new tag checksum and store it in the .git/ directory of the project's repo.

```git tag v1.4-lw```{{execute}}

Go ahead and create few other tags with;

```git tag v1.4-rc```{{execute}}

```git tag v1.5-rc```{{execute}}

```git tag -a v1.5 -m "my version 1.5"```{{execute}}

### Listing Tags

To list stored tags in a repo execute the following:

```git tag```{{execute}}

Your repository my have lots of tags at some point in time, to refine the list of tags the `-l` option can be passed with a wild card expression:

```git tag -l *-rc```{{execute}}

Which uses the `-l` option and a wildcard expression of `*-rc` which returns a list of all tags marked with a **-rc** prefix, traditionally used to identify release candidates.

### Sharing: Pushing Tags to Remote

Sharing tags is similar to pushing branches. By default, `git push` will _not_ push tags. Tags have to be explicitly passed to git push.

```git push origin v1.4```{{execute}}

To push multiple tags simultaneously pass the `--tags` option to `git push` command. When another user clones or pulls a repo they will receive the new tags.

```git push origin --tags```{{execute}}

### Checking Out Tags

You can view the state of a repo at a tag by using the git checkout command.

```git checkout v1.4```{{execute}}

Which will checkout the v1.4 tag. This puts the repo in a detached `HEAD` state. This means any changes made will not update the tag. They will create a new detached commit. This new detached commit will not be part of any branch and will only be reachable directly by the commits SHA hash.

Return back to the master branch using ```git checkout master```{{execute}}.

### Deleting Tags

Deleting tags is a straightforward operation. Passing the `-d` option and a tag identifier to git tag will delete the identified tag.

```git tag```{{execute}}

```git tag -d v1.4-lw```{{execute}}

## Protip

* As a best practice try create a new branch anytime you're making changes in a detached `HEAD` state.