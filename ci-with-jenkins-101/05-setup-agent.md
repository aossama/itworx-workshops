Once the plugins have been installed, you can configure how they launch the Docker Containers. The configuration will tell the plugin which Docker Image to use for the agent and which Docker daemon to run the containers and builds on.

The plugin treats Docker as a cloud provider, spinning up containers as and when the build requires them.

## Task

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

Click **Docker Agent templates...** and then **Add Docker Template**. You can now configure the container options.
Set the label of the agent to docker-agent. This is used by the Jenkins builds to indicate it should be built via the Docker Agent we're defining.
Make sure it is **Enabled**.
For the **Docker Image**, use benhall/dind-jenkins-agent:v2. This image is configured with a Docker client
Under **Container Settings**, In the "Volumes" text box enter /var/run/docker.sock:/var/run/docker.sock. This allows our build container to communicate with the host.
For **Connect Method** select Connect with SSH. The image is based on the Jenkins SSH Slave image meaning the default Inject SSH key will handle the authenication.
Click **Save**.

Jenkins can now start a **Build Agent** as a container when required.
