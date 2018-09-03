In this step we'll get exposed to more options around interacting with containers. We'll get more familiar with inspecting containers metadata, viewing containers log and managing containers.

In this step We will see how to:

* Check the logs of a container
* Stop a container
* Inspect containers

## Task

### Starting more containers

Let's start some more containers.

```docker container run -d aossama/clock```{{execute}}

```docker container run --name yacc -d aossama/clock```{{execute}}

Check that ```docker container ls```{{execute}} correctly reports all containers.

### View the logs of a container

Docker is already logging the standard output of the containers. Let's see these logs now;

```docker container logs yacc```{{execute}}

* We specified a name of the container.
* You can, of course, specify the container's short or full ID.
* The `logs` command will output the entire logs of the container.
  (Sometimes, that will be too much. Let's see how to address that.)

To avoid being spammed with eleventy pages of output, we can use the `--tail` option:

```docker container logs --tail 5 yacc```{{execute}}

* The parameter is the number of lines that we want to see.

We can follow the logs of our container:

```docker container logs --tail 1 --follow yacc```{{execute}}

* This will display the last line in the log file.
* Then, it will continue to display the logs in real time.
* Use ^C to exit.

### Stopping Containers

There are two ways we can terminate our detached container.

* Killing it using the `docker kill` command. This one stops the container immediately, by using the KILL signal.
* Stopping it using the `docker stop` command. Stopping is more graceful. It sends a TERM signal, and after 10 seconds, if the container has not stopped, it sends KILL.

Reminder: the KILL signal cannot be intercepted, and will forcibly terminate the container.

Let's stop one of those containers:

```docker container stop yacc```{{execute}}

This will take few seconds:

* Docker sends the TERM signal;
* the container doesn't react to this signal (it's a simple Shell script with no special signal handling);
* few seconds later, since the container is still running, Docker sends the KILL signal;
* this terminates the container.
