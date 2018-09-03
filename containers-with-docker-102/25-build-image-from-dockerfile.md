Docker can build images automatically by reading the instructions from a file called `Dockerfile`. `Dockerfile` is a text file that contains all the commands needed to build a given image.

`Dockerfiles` adhere to a specific format and use a specific set of instructions. This lab covers the best practices and methods recommended by Docker for building efficient images.

Below are some dockerfile instructions which can be used in a `Dockerfile`:

* **FROM**: The base image for building a new image. This command must be on top of the dockerfile.
* **RUN**: Used to execute a command during the build process of the docker image.
* **ADD**: Copy a file from the host machine to the new docker image.
* **ENV**: Define an environment variable.
* **CMD**: Used for executing commands when we build a new container from the docker image.
* **ENTRYPOINT**: Define the default command that will be executed when the container is running.
* **WORKDIR**: This is directive for CMD command to be executed.
* **VOLUME**: Enable access/linked directory between the container and the host machine.

Lets get started with creating Dockerfiles. Create a new directory;

```mkdir myimages```{{execute}}

```cd myimages```{{execute}}

Then create a new `./myimages/Dockerfile`{{open}} file adding to it the below content

<pre class="file" data-filename="./myimages/Dockerfile" data-target="replace">
#FROM - Image to start building on.
FROM ubuntu:14.04

#MAINTAINER - Identifies the maintainer of the dockerfile.
MAINTAINER user@example.com

#RUN - Runs a command in the container
RUN echo "Hello world" > /root/hello_world.txt

#CMD - Identifies the command that should be used by default when running the image as a container.
CMD ["cat", "/root/hello_world.txt"]
</pre>

Then create a new image using the **Dockerfile** to build it;

```docker build -t hello:v1 .```{{execute}}

Inspect the images

```docker image ls | grep hello```{{execute}}

Finally, lets test our image by run a container from it:

```docker run -it --rm --name hello hello:v1```{{execute}}

