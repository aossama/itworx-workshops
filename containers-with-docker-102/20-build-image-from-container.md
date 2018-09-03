Docker makes it easy to develop and deploy custom and consistent environments that include specific applications and dependencies.

Lets run a new container for webserver which we will edit to have our customized image:

```docker container run --name webserver -p 8000:80 nginx:latest```{{execute}}

After creating the container, we need to attach to it in order to make some changes, type this command:

```docker exec -it webserver /bin/bash```{{execute}}

To visualize the changes, lets edit the welcome page of nginx to be "Welcome from our server":

```echo "Welcome from our server" > /usr/share/nginx/html/index.html```{{execute}}

Type ```exit```{{execute}} to get out of the container, run this command to call the server ip:

```curl http://localhost:8000```{{execute}}

### Commit Changes to the Image

Next, save the container as an image with the docker commit command:

```docker commit webserver new-webserver```{{execute}}

If you run the docker images command, you’ll see the new image, new-webserver listed.

### Tag Your Image for Version Control

When you pull down an image from Docker Hub, the Status line includes the image tag as shown here:

Status: Downloaded newer image for nginx:latest

Docker tags are an easy way for you to know what version or release you are working with. This is especially useful for creating new images from a base image. For example, if you have a Ubuntu image you use as a base to create different images, Docker tags help you track the differences:

new-webserver:v1.8.10.2017
new-webserver:v2.8.10.2017
new-webserver:v3.8.10.2017

Create image tags with a docker commit. Using the example tags above, tag the new image with a version number and date:

```docker commit new-webserver new-webserver:v1.8.10.2017```{{execute}}

Run docker images to see the new image created along with the associated tag.

### Push Your Image to Docker Hub

Before pushing the image to Docker Hub, add a description, your full name (FULL NAME in the example here), and Docker Hub username (USERNAME) in the docker commit:

docker commit -m "Added new web Server" -a "FULL NAME" webserver USERNAME/new-webserver-template:v1.8.10.2017

Once this is fully tagged, log in and push it to Docker Hub:

You will be prompted for your Docker Hub credentials. When authentication succeeds, you will see Login succeeded. Now, you can push the image to the Hub with the command:

```docker push new-websrver-template:v1.8.10.2017```{{execute}}

Open a browser, log in to your Docker Hub account, and go your main repository. You will see the new image listed. Click on the image and then click on the Tags tab to see the added tag:

