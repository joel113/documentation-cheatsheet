# Docker Cheat Sheet

## Run

`docker run --rm -it --entrypoint /bin/sh busybox` - Runs the shell in a disposable images container  

`docker run -t -i alpine` - Runs alpine linux in tty mode with STDIN open even if not attached, often `-t -i` is written as `-it`

`docker run --name nginx -d -p 8080:80 nginx` Runs nginx in detached mode with port 8080 mapped to the host

`docker run --name openjdk -d openjdk` - Runs openjdk in detached mode with the name openjdk

`docker run -a stdin -a stdout -it ubuntu /bin/bash` - Runs an ubuntu image and select Docker attach to both stdout and stderr

`docker run amazoncorreto:17 java --version` - Runs amazon correto and prints the java version

`docker run -it -e FOO=BAR -t image_tag_name_and_version` - Runs an image and passes the environmental variable FOO with the value BAR

[Docker Run Reference](https://docs.docker.com/engine/reference/run/)

## Exec

`docker exec -it broker bash` - Runs an interactive command in the broker container

`docker exec -d ubuntu touch /tmp/whatever` - Runs a detached command in the ubuntu container

## Build

`docker build -t hello-world .` - Builds and tags a new image from a Dockerfile

`docker run hello-world` - Runs the new image called hello world

[Docker Build Reference](https://docs.docker.com/engine/reference/commandline/build/)
 
## Help

`nerdctl run --help` - Prints the command line arguments of nerdctl run if you use nerdctl instead of the docker cli

## Images

`docker images --no-trunc --quiet datadog/agent:7-jmx` - Shows non truncated information about an image

## Pull

`docker pull datadog/agent:7-jmx` - Pulls an image

## Inspect

`docker inspect datadog/agent:7-jmx` - Inspects an image

`docker inspect --format='{{.RepoDigests}}' gcr.io/alpha/homeapp:latest` - Shows the repository hash of an image

`dive openjdk:17` - Inspects the layers of an image using the dive tool

`syft openjdk:17` - Generates a software bill of materiales of container images using the syft tool

## Dockerfile

```
FROM openjdk:17

COPY testprj-1.0-SNAPSHOT.jar /home/testprj-1.0-SNAPSHOT.jar
CMD ["java","-jar","/home/testprj-1.0-SNAPSHOT.jar"]
```

```
FROM openjdk:17

COPY Hello.java .

RUN javac Hello.java

CMD ["java", "Hello"]
```

```
FROM amazoncorretto:17

RUN echo $' \
public class Hello { \
public static void main(String[] args) { \
System.out.println("Welcome to Amazon Corretto!"); \
} \
}' > Hello.java

RUN javac Hello.java

CMD ["java", "Hello"] 
```

```
FROM golang:1.16-alpine

WORKDIR /app

COPY go.mod ./
COPY go.sum ./

RUN go mod downlaod

COPY *.go ./

RUN go build -o /docker-gs-ping

CMD [ "/docker-gs-ping" ]
```

`FROM <image>` - Initializes a new build stage and sets the base image for the subsequent instructions

`RUN <command>` - Executes any command in a new layer on top of the current image and commit the results

`CMD <command> <param1> <param2>` - Provides a default for executing the container

`LABEL <key>=<value>` - Adds metadata to an image

`EXPOSE <port>` - Informs the container runtime that the container listens on the specific network port at runtime

`EXPOSE <port>/<protocol>` - Allows to specify whether the container listens for udp or tcp connections

`ENV <key>=<value>` - Sets the environment variable key to the value <value>

`ADD <src> ... <dest>` - Copies new files, directories or remote files to the filesystem of the image at the path <dest>

`ADD --chown=bin files* /somedir/` - The `--chown`flag specifies the given username, groupname, or uid / gid combination to request specific ownership of the content added as all new files or directories are created with a uid and gid 0 by default

`COPY <src> ... <dest>` - Copies new files, directories or remote files to the filesystem of the image at the path <dest>

`ENTRYPONT ["executable","param1","param2"]` - Executable form of an `ENTRYPOINT` which configures a container that will run as an executable

`ENTRYPOINT command param1 param2` - Shell form of an `ENTRYPOINT`

## BOM

`docker sbom alpine:latest` - Calculates the bill of materials of the latest alpine image

## Cleanup

`nerdctl rm -f $(nerdctl ps -a -q)` - Removes all containers

`nerdctl volume rm -f $(nerdctl volume ls -q)` - Remove all volumes
