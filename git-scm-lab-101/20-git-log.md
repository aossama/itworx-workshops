The purpose of any version control system is to record changes to your code. This gives you the power to go back into your project history to see who contributed what, figure out where bugs were introduced, and revert problematic changes.

## Task

### Reviewing the repository log

Optimally when you want to review the history of the repository, you'll use ```git log```{{exeucte}}. This show the commit logs on the tree you are currently standing at.

### Condense log output

The `--oneline` flag condenses each commit to a single line. By default, it displays only the commit ID and the first line of the commit message. Your typical ```git log --oneline```{{execute}} output will look something like this:

<pre>
0e25143 Merge branch 'feature'
ad8621a Fix a bug in the feature
16b36c6 Add a new feature
23ad9ad Add the initial code base
</pre>

### Draw ASCII Graph

The `--graph` option draws an ASCII graph representing the branch structure of the commit history. This is commonly used in conjunction with the `--oneline` and `--decorate` commands to make it easier to see which commit belongs to which branch:

```git log --graph --oneline --decorate```{{execute}}

### Custom Formatting

For all of your other `git log` formatting needs, you can use the `--pretty=format:"<string>"` option. This lets you display each commit however you want using printf-style placeholders. For example, the `%cn`, `%h` and `%cd` characters in the following command are replaced with the committer name, abbreviated commit hash, and the committer date, respectively.

```git log --pretty=format:"%cn committed %h on %cd"```{{execute}}

### Filter logs by amount

The most basic filtering option for `git log` is to limit the number of commits that are displayed. When you are only interested in the last few commits, this saves you the trouble of viewing all the commits in a page.

You can limit `git log` output by including the `-<n>` option. For example, the following command will display only the 3 most recent commits.

```git log -3```{{execute}}

### Filter logs by date

If you are looking for a commit from a specific time frame, you can use the `--after` or `--before` flags for filtering commits by date. These both accept a variety of date formats as a parameter. For example, the following command only shows commits that were created after July 1st, 2014 (inclusive):

```git log --after="2017-12-10"```{{execute}}

You can also pass in relative references like "1 week ago" and "yesterday":

```git log --after="10 minutes ago"```{{execute}}

To search for a commits that were created between two dates, you can provide both a --before and --after date. For instance, to display all the commits added between July 1st, 2014 and July 4th, 2014, you would use the following:

```git log --after="2017-10-10" --before="2017-12-10"```{{execute}}

### Filter by author

When you are only looking for commits created by a particular user, use the `--author` flag. This accepts a regular expression, and returns all commits whose author matches that pattern. If you know exactly who you are looking for, you can use a plain old string instead of a regular expression:

```git log --author="Ahmed"```{{execute}}
