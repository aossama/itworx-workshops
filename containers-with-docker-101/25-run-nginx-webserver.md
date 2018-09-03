In this step we'll run an Nginx webserver and expose some static content from this server.

## Task

### Find the nginx Image

```docker search nginx```{{execute}}

### Run the nginx Container

```docker container run --name webserver -p 8000:80 nginx:latest```{{execute}}

To run the nginx webserver and attach to the foreground.

### Open the container in a browser tab



### Inspect the nginx Container

The command ```docker container inspect <friendly-name|container-id>``` provides more details about a running container, such as IP address.

```docker container inspect mydb```{{execute}}

The command ```docker container logs <friendly-name|container-id>``` will display messages the container has written to standard error or standard out.

