Let's create a new branch from GitLab, fetch it to our local working directory, modify it and save the changes.

## Task

### Create Branch on GitLab

1. In your project dashboard, choose **Repository** then go to **Branches**. This will open the branches page where 
you can manage all your project branches.
2. Create a **New branch**, giving it name "feature-01"

### Start working on the new Branch

From the terminal window, pull the latest content from the upstream repository with;

```git pull```{{execute}}

Which will show you that you downloaded the remote branch localy.

<pre>
From http://git.itworx.cloud/aossama/blaa
 * [new branch]      feature-01 -> origin/feature-01
Already up-to-date.
</pre>

Now checkout the new branch;

```git checkout feature-01```{{execute}}

<pre>
Branch feature-01 set up to track remote branch feature-01 from origin.
Switched to a new branch 'feature-01'
</pre>

And start introducing some changes to the branch by editing the file `app.js`{{open}} and adding the content;

<pre class="file" data-filename="./app.js" data-target="replace">
const express = require('express')
const app = express()

// Landing page
app.get('/', (req, res) => res.send('Hello World!'))

// About us page
app.get('/about', (req, res) => res.send('Yet another about us page!'))

app.listen(3000, () => console.log('Example app listening on port 3000!'))
</pre>

### Save Changes and Push

Add, commit and push the modified content;

```git commit -a -m "Add feature 1"```{{execute}}

```git push```{{execute}}

At this point will detect that you divereged the history, and will remind you that you may need to create a merge request.