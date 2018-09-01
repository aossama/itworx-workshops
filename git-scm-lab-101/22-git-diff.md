Diffing is a function that takes two input data sets and outputs the changes between them. `git diff` is a multi-use Git command that when executed runs a diff function on Git data sources. These data sources can be commits, branches, files and more. This document will discuss common invocations of `git diff` and diffing work flow patterns. The `git diff` command is often used along with `git status` and `git log` to analyze the current state of a Git repo.

## Task

### Modify README.md and check diff

Now let's introduct some changes in our initial repository layout and inspect the difference using `git diff`. Open `README.md`{{open}} file and add some content to it;

<pre class="file" data-filename="./README.md" data-target="replace">
# Simple HTML Project

This is a simple HTML project tracked by git.

Adding some new content to inspect how git diff works.
</pre>

Once the new content has been added, inspect the output of ```git status```{{execute}}, which will tell you that the `README.md` file has been modified. Now let's inspect this modifications by using;

```git diff README.me```{{execute}}

Let us now examine a more detailed breakdown of the diff output.

#### Comparison input

<pre>diff --git a/README.md b/README.md</pre>

This line displays the input sources of the diff. We can see that a/diff_test.txt and b/diff_test.txt have been passed to the diff.

#### Meta data

<pre>index 6b0c6cf..b37e70a 100644</pre>

This line displays some internal Git metadata. You will most likely not need this information. The numbers in this output correspond to Git object version hash identifiers.

#### Markers for changes

<pre>
--- a/README.md
+++ b/README.md
</pre>

These lines are a legend that assigns symbols to each diff input source. In this case, changes from a/diff_test.txt are marked with a --- and the changes from b/diff_test.txt are marked with the +++ symbol.

#### Diff chunks

The remaining diff output is a list of diff 'chunks'. A diff only displays the sections of the file that have changes. In our current example, we only have one chunk as we are working with a simple scenario. Chunks have their own granular output semantics.

@@ -1 +1 @@
-this is a git diff test example
+this is a diff example

The first line is the chunk header. Each chunk is prepended by a header inclosed within @@ symbols. The content of the header is a summary of changes made to the file. In our simplified example, we have -1 +1 meaning line one had changes. In a more realistic diff, you would see a header like:

@@ -34,6 +34,8 @@

In this header example, 6 lines have been extracted starting from line number 34. Additionally, 8 lines have been added starting at line number 34.

The remaining content of the diff chunk displays the recent changes. Each changed line is prepended with a + or - symbol indicating which version of the diff input the changes come from. As we previously discussed, - indicates changes from the a/diff_test.txt and + indicates changes from b/diff_test.txt.

### Highlighting changes

`git diff` also has a special mode for highlighting changes with much better granularity: `‐‐color-words`. This mode tokenizes added and removed lines by whitespace and then diffs those.

```git diff --color-words```{{execute}}

### Comparing all changes

Invoking ```git diff```{{execute}} without a file path will compare changes across the entire repository. The above, file specific examples, can be invoked without the `README.md` argument and have the same output results across all files in the local repo.

## Protip

