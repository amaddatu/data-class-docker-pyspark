
# Goal:

Create a dockerized container solution that will run on any platform. It should be able to run a particular pyspark and jupiter notebook solution. I will simply install a particular odbc driver for postgres later and then add another container to support a postgres database.

## Software:

Virtual Box - for all computers without a native docker install (Most windows users not on win pro)
virtualbox.org

Alpine Linux - image so that we have a micro operating system to install as a docker host
https://alpinelinux.org/downloads/

Docker - a container solution that will allow us to run pre-built software containers for our purpose
https://wiki.alpinelinux.org/wiki/Docker

Docker-Compose - a container configuration solution (it allows us to build a configuration file - but I like to call it a recipe)
https://wiki.alpinelinux.org/wiki/Docker

## Docker containers needed:

Pyspark and Jupyter notebook container...
https://hub.docker.com/r/jupyter/pyspark-notebook/

odbc install instructions for alpine...
https://stackoverflow.com/questions/51888064/install-odbc-driver-in-alpine-linux-docker-container

postgres container...
https://hub.docker.com/_/postgres
