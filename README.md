
## About

  The image generated by this project can be used as an empty debian 
  container or as base image for other Docker images.

  Jens Kleinhout
  HKdigital

## Installation

  1) Clone the repository

      git clone git@bitbucket.org:hkdigital/debian-slim-2021a.git

### Build docker image

      ./build-latest-image.sh

## Howto

### What does this container do?

When you run a container that was created from this image, by default it will run the command "sleep infinity".

So the container runs a never ending process, that does nothing.

If you want to do something more useful, you should specify a COMMAND to execute.

### How does it work?

E.g. the following command runs a container

    docker run --rm debian-slim-2021a

This command will run the script [/srv/boot.sh] inside the container, which in turn will execute the script [/srv/run.sh].

By default run.sh will execute the command "sleep infinity".

Press ctrl-c to quit

## Use cases

### Run bash shell inside the container

Run the following command to run an interactive bash shell:

    docker run -t -i --rm debian-slim-2021a bash

Exactly this is done in the included script [run-tmp-bash-container.sh]

### Run using docker-compose

Below an example of using the image in a docker-compose file

```yaml
    version: "3"

    services:
      debian:
        image: debian-slim-2021a
```

### Run bash in a running container (docker-compose)

Run the following command to run [bash] inside the container

    docker-compose exec <service-name> bash

