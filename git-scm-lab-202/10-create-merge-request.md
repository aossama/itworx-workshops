## Task

### Create a Merge request

Merge requests are useful to integrate separate changes that you've made to a project, on different branches. This is a brief guide on how to create a merge request. There are several ways to open a Merge request, one of which;

1. Go to the **Branches** page again on GitLab server.
2. You'll notice a new button called **Merge request**, which simplifies your work to open a merge request. Click on **Merge request** button.
3. Leave the values on the **New Merge Request** as their defaults, and click on **Submit merge request**.

Your merge request will be ready to be approved and merged.

### Review, Approve and Merge

Merge request approvals enable enforced code review by requiring specified people to approve a merge request before it can be unblocked for merging.

1. Review the _Commits_ and _Changes_ on the Merge request page.
2. Optionally you can specify that the source branch be removed upon it's merge.
3. When satisfied with the merge request, go ahead and click on **Merge** button.

This will cause a new commit on the master branch with the content of the _feature-01_ branch.

### Pull Latest Content

Now as the master has changed on the remote upstream repository, you'll need to pull the latest changes on your local repository. Use;

```git checkout master```{{execute}}

```git pull```{{execute}}

To download and update your working directory to the latest changes on the repository.