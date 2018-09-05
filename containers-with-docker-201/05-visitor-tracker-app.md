In this step we'll learn how to build a simple Python application in it's own image. Then we'll configure 
the application to use a Redis container to track the number of our visitors.

## Task

### Create Redis Container

Start by preparing our Redis database which will be used to track the number of visitors on our page;

```docker run -d --name visitors-counter redis```{{execute}}

### Build the Application

Use the following command to clone the application source code from GitHub (you can click the command or 
manually type it). This will make a copy of the lab’s repo in current working directory;

```git clone https://github.com/aossama/simple_counter.git .```{{execute}}

Inspect the `Dockerfile`;

```cat Dockerfile```{{execute}}

Then build the image;

```docker build -t counter:0.1 .```{{execute}}

Note that we are tagging our image with 0.1 as this is the initial release of our image.

### Verify the Application

Run a new container from the application;

```docker run -d --rm --publish 8010:8080 --name tmp_counter counter:0.1```{{execute}}

Then navigate to https://[[HOST_SUBDOMAIN]]-8010-[[KATACODA_HOST]].environments.katacoda.com/ and notice 
that the **Visits:** counter cannot connect to a Redis instance to track the number of visits on our page.

Stop the application:

```docker stop tmp_counter```{{execute}}

### Link Application with Redis

Now let's fix this connectivity issue between our container and Redis database. Run new instances of the 
application and linking them to the Redis database container.

```docker run -d --name visitors01 --publish 8081:8080 --link visitors-counter:redis counter:0.1```{{execute}}

```docker run -d --name visitors02 --publish 8082:8080 --link visitors-counter:redis counter:0.1```{{execute}}

```docker run -d --name visitors03 --publish 8083:8080 --link visitors-counter:redis counter:0.1```{{execute}}

Now you created three containers each listening on it's own port, but all of them connects and store their 
visitors count on the Redis server.

You can navigate to:

* https://[[HOST_SUBDOMAIN]]-8081-[[KATACODA_HOST]].environments.katacoda.com/
* https://[[HOST_SUBDOMAIN]]-8082-[[KATACODA_HOST]].environments.katacoda.com/
* https://[[HOST_SUBDOMAIN]]-8083-[[KATACODA_HOST]].environments.katacoda.com/

Notice the the visitors count is being incremented each time you visit the any of the pages.