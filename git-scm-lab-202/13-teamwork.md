Collaborating with others is the essence of a source code management system. In this step you'll have to find a college and collaborate with him/her using GitLab Issue tracker. The GitLab Issue Tracker is an advanced and complete tool for tracking the evolution of a new idea or the process of solving a problem.

It allows you, your team, and your collaborators to share and discuss proposals before and while implementing them.

## Task

### Create an Issue

1. In the project dashboard, go to **Issues**, then click on **New issue**. This will open the **New Issue** form.
2. Fill in the form with the below information;

   Title: Add contact page
   Description: Our customer needs his website visitor a contact us page. Let's create a page to handle his visitors.
   Assignee: Choose your college's name from the drop down list

3. Click on **Submit issue**

### Teamwork

Ask your college to start inspecting and working on the new issue which has just been created.

* Your college must navigate to the issue that you've just created and assigned it to him/her.
* Create a new branch from the issues page by expanding the drop down menu beside **Create merge request** button.
* For the new branch name, use **contact-us**
* Click on **Create merge request**

At this point, the college must clone your repository and work on the new **contact-us** branch.

* They should be able to clone the repository in a new directory using; ```git clone http://git.itworx.cloud/<username>/project-atomic.git ./another-project-atomic/```
* Change directory to ```cd another-project-atomic/```{{execute}}
* Edit the file `another-project-atomic/app.js`{{open}} with content;

<pre class="file" data-filename="./another-project-atomic/app.js" data-target="replace">
const express = require('express')
const app = express()

// Landing page
app.get('/', (req, res) => res.send('Hello World!'))

// About us page
app.get('/about', (req, res) => res.send('Yet another about us page!'))

// Content page
app.get('/about', (req, res) => res.send('You can send us an email on contact@example.com'))

app.listen(3000, () => console.log('Example app listening on port 3000!'))
</pre>

* Add, commit and push the modified content.

### Review, Approve and Merge

1. Review the _Commits_ and _Changes_ on the Merge request page.
2. Optionally you can specify that the source branch be removed upon it's merge.
3. When satisfied with the merge request, go ahead and click on **Merge** button.

This will cause a new commit on the master branch with the content of the _contact-us_ branch.

### Pull Latest Content

Now as the master has changed on the remote upstream repository, you'll need to pull the latest changes on your local repository. Use;

```cd ../```{{execute}}

```git checkout master```{{execute}}

```git pull```{{execute}}

To download and update your working directory to the latest changes on the repository.