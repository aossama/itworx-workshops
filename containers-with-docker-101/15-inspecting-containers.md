In this step we'll get exposed to more options around interacting with containers. We'll get more familiar with inspecting containers metadata, viewing containers log and stopping containers.

## Inspect Running Containers

To check the currently running containers, use;

```docker container ls```{{execute}}

Docker tells us:

* The (truncated) ID of our container.
* The image used to start the container.
* That our container has been running (Up) for a couple of minutes.
* Other information (COMMAND, PORTS, NAMES) that we will explain later.

Now let's display detailed information on one or more containers;

```docker container inspect mydb```{{execute}}

```docker container inspect --format='{{.NetworkSettings.Networks.bridge.IPAddress}}' mydb```{{execute}}

```docker container inspect mydb | grep IPAddress```{{execute}}

## Starting more containers

Let's start two more containers.

```docker container run -d aossama/clock```{{execute}}

```docker container run --name yacc -d aossama/clock```{{execute}}

Check that ```docker container ls``` correctly reports all 3 containers.

## View the logs of a container

Docker is already logging the standard output of the containers. Let's see these logs now;

```docker container logs yacc```{{execute}}

* We specified a prefix of the full container ID.
* You can, of course, specify the full ID.
* The logs command will output the entire logs of the container.
  (Sometimes, that will be too much. Let's see how to address that.)

To avoid being spammed with eleventy pages of output, we can use the --tail option:

```docker container logs --tail 5 yacc```{{execute}}

* The parameter is the number of lines that we want to see.

We can follow the logs of our container:

```docker container logs --tail 1 --follow yacc```{{execute}}

* This will display the last line in the log file.
* Then, it will continue to display the logs in real time.
* Use ^C to exit.

## Stopping Containers

There are two ways we can terminate our detached container.

* Killing it using the docker kill command.
* Stopping it using the docker stop command.

The first one stops the container immediately, by using the KILL signal.

The second one is more graceful. It sends a TERM signal, and after 10 seconds, if the container has not stopped, it sends KILL.

Reminder: the KILL signal cannot be intercepted, and will forcibly terminate the container.

Let's stop one of those containers:

```docker container stop yacc```{{execute}}

This will take 10 seconds:

* Docker sends the TERM signal;
* the container doesn't react to this signal (it's a simple Shell script with no special signal handling);
* 10 seconds later, since the container is still running, Docker sends the KILL signal;
* this terminates the container.
