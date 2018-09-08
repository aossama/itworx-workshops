In this step we will create a new project which Jenkins will build via our new agent. The project source code is at https://github.com/aossama/simple-html-app. The repository has a Dockerfile; this defines the instructions on how to produce the Docker Image. Jenkins doesn't need to know the details of how our project is built.

## Task

### Create New Job

* On the Jenkins dashboard, select **Create new jobs**
* Give the job a friendly name such as **Jenkins Demo**, select **Freestyle project** then click OK.
* The build will depend on having access to Docker. Using the "Restrict where this project can be run" we can define the label we set of our configured Docker agent. Set "Label Expression" to docker-agent. You should have a configuration of "Label is serviced by no nodes and 1 cloud".

If you see the error message There's no agent/cloud that matches this assignment. Did you mean ‘master’ instead of ‘docker-agent’?, then the Docker plugin and the Docker Agent has not been Enabled. Go back to configure the system options and enable both checkboxes.

* Select the Repository type as **Git** and set the **Repository URL** to be https://github.com/aossama/simple-html-app.git.
* We can now add a new build step using the **Add Build Step** dropdown. Select **Execute Shell**.

Because the logical of how to build is specified in our Dockerfile, Jenkins only needs to call build and specify a friendly name. In this lab, use the following commands;

<pre>
ls
docker info
docker build -t katacoda/jenkins-demo:${BUILD_NUMBER} .
docker tag katacoda/jenkins-demo:${BUILD_NUMBER} katacoda/jenkins-demo:latest
docker images
</pre>

The first stage lists all the files in the directory which will be built. When calling docker build we use the Jenkins build number as the image tag. This allows us to version our Docker Images. We also tag the build with latest.

At this point, or in an additional step, you could execute a docker push to upload the image to a centralised Docker Registry.

Our build is now complete. Click **Apply** then **Save**.

### Build Project

We now have a configured job that will build Docker Images based on our Git repository. The next stage is to test and try it.

On the left-hand side, select **Build Now**. You should see a build scheduled with a message "(pending—Waiting for next available executor)".

In the background, Jenkins is launching the container and connecting to it via SSH. Sometimes this can take a while to configure the Docker Agent. The error "(pending—Jenkins doesn’t have label docker-agent)" is while Jenkins waits for the Docker Agent to start.

You can see the progress using ```docker logs --tail=10 jenkins```{{execute}}

It's normal for this to take a few moments to complete.

### View Console Output

Once the build has completed you should see the Image and Tags using the Docker CLI docker images.

What was built into the Docker Image was a small HTTP server. You can launch it using: docker run -d -p 80:80 katacoda/jenkins-demo:latest

Using cURL you should see the server respond: curl host01

Jenkins will have the console output of our build, available via the dashboard. You should be able to access it below:

https://2886795298-8080-cykoria03.environments.katacoda.com/job/Katacoda%20Jenkins%20Demo/1/console

If you rebuilt the project, you would see a version 2 image created and the :latest tag reattached.