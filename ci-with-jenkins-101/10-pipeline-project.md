In this step we will create another project using the Pipeline feature in Jenkins. We will use the same source code which comes with a Jenkinsfile. Creating a Jenkinsfile, which is checked into source control, provides a number of immediate benefits:

* Code review/iteration on the Pipeline
* Audit trail for the Pipeline
* Single source of truth for the Pipeline, which can be viewed and edited by multiple members of the project.

## Task

### Create New Job

* On the Jenkins dashboard, select **Create new jobs**
* Give the job a friendly name such as **Jenkins Pipeline Demo**, select **Pipeline** then click OK.
* Under _Pipeline_ section, for **Definition** choose **Pipeline script from SCM**.
* Then choose **Git** as the SCM.
* In the repository URL, enter https://github.com/aossama/simple-html-app.git

### Build Project

We now have a configured job that will build Docker Images based on our Git repository. The next stage is to test and try it.

On the left-hand side, select **Build Now**. You should see a build scheduled with a message "(pending—Waiting for next available executor)".

In the background, Jenkins is launching the container and connecting to it via SSH. Sometimes this can take a while to configure the Docker Agent. The error "(pending—Jenkins doesn’t have label docker-agent)" is while Jenkins waits for the Docker Agent to start.

You can see the progress using ```docker logs --tail=10 jenkins```{{execute}}

It's normal for this to take a few moments to complete.

### View Console Output

Once the build has completed you should see the Image and Tags using the Docker CLI docker images. What was built into the Docker Image was a small HTTP server with a tiny HTML application. You can launch it using: 

```docker run -d -p 8001:80 jenkins-demo:latest```{{execute}

Jenkins will have the console output of our build, available via the dashboard. You should be able to access it below:

https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/job/Jenkins%20Pipeline%20Demo/1/console

If you rebuilt the project, you would see a version 3 image created and the :latest tag reattached.