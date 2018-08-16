In this step we'll run an Nginx webserver and expose some static content from this server.

## Task

### Find the nginx Image

```docker search nginx```{{execute}}

### Run the nginx Container

Use;

```docker container run --name webserver -p 8000:80 nginx:latest```{{execute}}

To run the nginx webserver and attach to the foreground.

### Open the container in a browser tab



### Inspect the nginx Container

The command ```docker container inspect <friendly-name|container-id>``` provides more details about a running container, such as IP address.

```docker container inspect mydb```{{execute}}

The command ```docker container logs <friendly-name|container-id>``` will display messages the container has written to standard error or standard out.

```docker container logs mydb```{{execute}}

This will output lots of lines, which are basically the logs from the application running inside the container and the processes running inside the container:

```docker container top mydb```{{execute}}

Although MySQL is running, it is isolated within the container because no network ports have been published to the host. Network traffic cannot reach containers from the host unless ports are explicitly published.

### Accessing nginx

Now that our MySQL database is up and running, we need to access it. If a service needs to be accessible by a process not running in a container, then the port needs to be exposed via the Host. Once exposed, it is possible to access the process as if it were running on the host OS itself. We know that by default, MySQL runs on port 3306.
