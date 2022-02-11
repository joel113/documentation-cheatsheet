# Docker Cheat Sheet

## Run and Exec

`docker exec -it broker bash` - Runs an interactive command in the broker container

`docker run --rm -it --entrypoint /bin/sh busybox` - Runs the shell in a disposable images container  

`docker run -t -i alpine` - Runs alpine linux

`docker run -t -i openjdk` - Runs openjdk

## Help

`nerdctl run --help` - Prints the command line arguments of nerdctl run if you use nerdctl instead of the docker cli

## Images

`docker images --no-trunc --quiet datadog/agent:7-jmx` - Shows non truncated information about an image

## Pull

`docker pull datadog/agent:7-jmx` - Pulls an image

## Inspect

`docker inspect datadog/agent:7-jmx` - Inspects an image

`docker inspect --format='{{.RepoDigests}}' gcr.io/alpha/homeapp:latest` - Shows the repository hash of an image
