In the first scenario, we discussed how you can start containers based on pre-existing images from the Docker Registry. This scenario explains how to build an image based on your requirements.

For this scenario, the container will be running a static HTML application using Nginx, a high-performance web server. In future, we'll explain how to deploy other stacks such as Node.js or Java.

Docker Images

Docker images are built based on a Dockerfile. A Dockerfile defines all the steps required to create a Docker image with your application configured and ready to be run as a container. The image itself contains everything, from operating system to dependencies and configuration required to run your application.

Having everything within the image allows you to migrate images between different environments and be confident that if it works in one environment, then it will work in another.

The Dockerfile allows for images to be composable, enabling users to extend existing images instead of building from scratch. By building on an existing image, you only need to define the steps to setup your application. The base images can be basic operating system installations or configured systems which simply need some additional customisations.

To help you complete the steps, an environment has been created with Docker configured. The editor allows you to write a Dockerfile which defines how to build the Docker image.