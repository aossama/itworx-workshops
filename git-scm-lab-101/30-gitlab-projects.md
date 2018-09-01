GitLab is a Git-based platform that integrates a great number of essential tools for software development and 
deployment, and project management:

* Code hosting in repositories with version control
* Track proposals for new implementations, bug reports, and feedback with a fully featured Issue Tracker
* Organize and prioritize with Issue Boards
* Code review in Merge Requests with live-preview changes per branch with Review Apps
* Build, test and deploy with built-in Continuous Integration
* Deploy your personal and professional static websites with GitLab Pages
* Integrate with Docker with GitLab Container Registry
* Track the development lifecycle with GitLab Cycle Analytics

GitLab is a self service hosted platform which enables you to create your own projects, administer the access to the 
repositories you own, create continous integration and delivery pipelines and more functions without the need to get 
back to operations team.

GitLab is a fully integrated software development platform that enables you and your team to work cohesively, faster, 
transparently, and effectively, since the discussion of a new idea until taking that idea to production all the way 
through, from within the same platform.

## Signup for a new GitLab account

In order to get going with the rest of this lab, you'll need to signup for a new account on the GitLab server which has 
been setup specifically setup for the workshops.

1. Navigate to http://git.itworx.cloud and register a new account
2. Login with the new account

## Projects

In GitLab, you can create projects for numerous reasons, such as, host your code, use it as an issue tracker, 
collaborate on code, and continuously build, test, and deploy your app with built-in GitLab CI/CD. Or, you can do it 
all at once, from one single project.

Projects can be available publicly, internally, or privately, at your choice. GitLab does not limit the number of 
private projects you create.

### Create a Project in GitLab

1. In your dashboard, click the green **New project** button or use the plus icon in the upper right corner of the navigation bar.

   ![New Project](assets/create_new_project_button.png)

2. This opens the **New project** page.

   ![New Project Info](assets/create_new_project_info.png)

3. Provide the following information:

   * Project name: simple-html-project
   * Project description: My simple HTML Project
   * Visibility Level: Public

4. Click **Create project**.

When you create a project in GitLab, you'll have access to a large number of features:

  * Repositories
  * Issues tracker
  * Merge Requests
  * GitLab CI/CD
  * Wiki
  * Code Snippets

### Sync repository remotely

Now that you've created an empty project on GitLab, you can now track the local repository to a remote one which can be used to collaborate work within a team.

In order to sync your repository to the remote one, you'll need to add the remote repository;

```git remote add origin http://git.itworx.cloud/<username>/simple-html-project.git```

And use the `git push` command to send your changes remotely;

```git push -u origin master```{{execute}}

## Outcome

* You have created a new project which can be used to sync your local git repository to it.
* You have syncronized your local repository to the remote GitLab repository.