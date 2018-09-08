Let's start this lab by preparing a new Jenkins instance.

## Task

### Launch Jenkins

Launch a new Jenkins instance as a Docker Container with the following command:

```docker run -d --name jenkins -p 8080:8080 -p 50000:50000 jenkins:alpine```{{execute}}

Port 8080 opens the Jekins web dashboard, 50000 is used to communicate with other Jenkins agents.

Then load Jenkins dashboard via the following URL https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/ . The username is **admin** and the password can be found from the output of the below command. On the terminal execute;

```docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword```{{execute}}

It may take a couple of seconds for Jenkins to finish starting and be available.

### Initial Jenkins Configuration

The first time you login to a new Jenkins instance, you are prompted to preset Jenkins configuration.

* Choose **Install Suggested Plugins**
* Wait until all plugins are installed.
* Fill the **Create First Admin Form** with the below:

  * Username: admin
  * Password: qwe123edc
  * Full name: Jenkins Admin
  * Email: admin@example.com

* Submit the form by clicking **Save and Finish**, and click on **Start using Jenkins**.

You will be redirected to Jenkins Dashboard.

### Install Docker Plugin

Now you'll use the dashboard to configure the plugins and start building Docker Images.

* Within the Dashboard, select **Manage Jenkins** on the left.
* On the Configuration page, select **Manage Plugins**.
* Manage Plugins page will give you a tabbed interface. Click **Available** to view all the Jenkins plugins that can be installed.
* Using the search box, search for **Docker**. There are multiple Docker plugins, select **Docker** using the checkbox.
* Click **Install without Restart** at the bottom.
* The plugins will now be downloaded and installed. Once complete, click the link **Go back to the top page**.

Your Jenkins server can now be configured to build Docker Images.

### Add Docker Agent

This step configures the plugin to communicate with a Docker host/daemon.

* Once again, select **Manage Jenkins**.
* Select **Configure System** to access the main Jenkins settings.
* At the bottom, there is a dropdown called **Add a new cloud**. Select **Docker** from the list.
* Make sure it is **Enabled**.
* The **Docker Host URI** is where Jenkins launches the agent container. In this case, we'll use the same daemon as running Jenkins, but you could split the two for scaling. Enter the URL tcp://172.17.0.11:2345
* Use **Test Connection** to verify Jenkins can talk to the Docker Daemon. You should see the Docker version number returned.

The Host IP address is the IP of your build agent / Docker Host.

### Configure Docker Agent Template

The Docker Agent Template is the Container which will be started to handle your build process.

* Click **Docker Agent templates...** and then **Add Docker Template**. You can now configure the container options.
* Set the label of the agent to docker-agent. This is used by the Jenkins builds to indicate it should be built via the Docker Agent we're defining.
* Make sure it is **Enabled**.
* For the **Docker Image**, use benhall/dind-jenkins-agent:v2. This image is configured with a Docker client
* Under **Container Settings**, In the "Volumes" text box enter /var/run/docker.sock:/var/run/docker.sock. This allows our build container to communicate with the host.
* For **Connect Method** select Connect with SSH. The image is based on the Jenkins SSH Slave image meaning the default Inject SSH key will handle the authenication.
* Click **Apply** then **Save**.

Jenkins can now start a **Build Agent** as a container when required.