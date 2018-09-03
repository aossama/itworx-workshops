Docker can build images automatically by reading the instructions from a Dockerfile, a text file that contains all the commands, in order, needed to build a given image. Dockerfiles adhere to a specific format and use a specific set of instructions. This lab covers the best practices and methods recommended by Docker for building efficient images.

Below are some dockerfile commands you must know:

### FROM
The base image for building a new image. This command must be on top of the dockerfile.

### RUN
Used to execute a command during the build process of the docker image.

### ADD
Copy a file from the host machine to the new docker image. There is an option to use an URL for the file, docker will then download that file to the destination directory.

### ENV
Define an environment variable.

### CMD
Used for executing commands when we build a new container from the docker image.

### ENTRYPOINT
Define the default command that will be executed when the container is running.

### WORKDIR
This is directive for CMD command to be executed.

### VOLUME
Enable access/linked directory between the container and the host machine.

Lets get our hands dirty with Dockerfils, create a new directory and a new and empty dockerfile inside that directory.

```mkdir myimages```{{execute}}
```cd myimages```{{execute}}
```touch Dockerfile```{{execute}}

File to be added:

#FROM - Image to start building on.
FROM ubuntu:14.04

#MAINTAINER - Identifies the maintainer of the dockerfile.
MAINTAINER user@example.com

#RUN - Runs a command in the container
RUN echo "Hello world" > /root/hello_world.txt

#CMD - Identifies the command that should be used by default when running the image as a container.
CMD ["cat", "/root/hello_world.txt"]

Now lets build our Dockerfile to create a new image:

```docker build -t hello:v1 .```{{execute}}

Lets check our images to find the newely created one:

```docker images```{{execute}}

Finally, lets test our image by run a container from it:

```docker run -it --rm --name hello hello:v1```{{execute}}

