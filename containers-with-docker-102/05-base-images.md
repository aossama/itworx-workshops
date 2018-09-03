All Docker images start from a base image. A base image is the same images from the Docker Registry which are used to start containers. Along with the image name, we can also include the image tag to indicate which particular version we want, by default, this is latest. These base images are used as the foundation for your additional changes to run your application.

## What is an image?

* Image = files + metadata
* These files form the root filesystem of our container.
* The metadata can indicate a number of things, e.g.:
  * the author of the image
  * the command to execute in the container when starting it
  * environment variables to be set
  * etc.
* Images are made of layers, conceptually stacked on top of each other.
* Each layer can add, change, and remove files and/or metadata.
* Images can share layers to optimize disk usage, transfer times, and memory use.

### Pull new image

To pull an ubuntu image from Docker official register, run the following command:

```docker pull ubuntu ```{{execute}}

To see the list of Docker images on the system, you can issue the following command:

```docker images```{{execute}}

From the above output, you can see that the server has one image which is ubuntu. Each image has the following attributes:

* TAG − This is used to logically tag images.
* Image ID − This is used to uniquely identify the image.
* Created − The number of days since the image was created.
* Virtual Size − The size of the image.

### Inspect the image

The command ```docker inspect  <image name:tag>``` provides more details about the downloaded image including Environment variables, the cmd that runs when the container created, etc.

```docker  inspect ubuntu:latest```{{execute}}
