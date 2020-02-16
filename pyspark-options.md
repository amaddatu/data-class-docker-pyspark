
# Goal:

Create a dockerized container solution that will run on any platform. It should be able to run a particular pyspark and jupiter notebook solution. I will simply install a particular odbc driver for postgres later and then add another container to support a postgres database.

# Background:

This was simply the most difficult week to solve all the problems. I believe I covered all my solutions here (please feel free to put it in order). Hope this is helpful.

## All options

1. Use the pyspark install instructions below, use the medium article and the ODBC driver (Must use java 1.8, no other java version is known to work)

2. Use docker-compose (separate file included) for a mac machine. The docker-compose file is really just plug and play. You just need to download the ODBC driver to the correct location. You will of course need docker and docker-compose on mac. (This may work on windows as well, but the file paths may need to change) The ports are 15432 for postgres and 8888 for jupyter-notebook. (use `docker-compose up` to start up the docker containers)

3. Use a VM. I used centos 7 minimal install for those machines that I simply could not figure out. I disabled selinux and used the epel-release repo to install docker and docker-compose. I exported the VM on a flash drive. All the student needed to do is map a shared folder to be the same as jupyterhome. When they need it, simply start the VM. I will send the docker-compose.yml with this guide. The ports are 15432 for postgres and 8888 for jupyter-notebook. Remote SSH (or any fileftp program) can be used in visual studio to seemlessly work with the VM and the files on the machine.

4. Use a hotspot for Zepl (this really works, but can be expensive for the student depending on their plan).

## Software:

Pyspark - The full instructions for pyspark installation (windows only)
https://medium.com/@naomi.fridman/install-pyspark-to-run-on-jupyter-notebook-on-windows-4ec2009de21f

Virtual Box - for all computers without a native docker install (Most windows users not on win pro)
virtualbox.org
https://www.virtualbox.org/wiki/Downloads


Docker - a container solution that will allow us to run pre-built software containers for our purpose
https://docs.docker.com/docker-for-mac/install/

Docker-Compose - a container configuration solution (it allows us to build a configuration file - but I like to call it a recipe)
https://docs.docker.com/compose/install/
Documentation - https://docs.docker.com/compose/


## Docker containers needed:

Pyspark and Jupyter notebook container...
https://hub.docker.com/r/jupyter/pyspark-notebook/

odbc install (useful for missing driver issues with postgres)...
https://jdbc.postgresql.org/download.html

postgres container...
https://hub.docker.com/_/postgres

The connection url to access the docker database should be like...
postgresql://database:5432/accounting_db


## Configuration needed for VM:

Centos needs the installer for docker and docker compose, the epel-release makes it easy
`yum install epel-release` 

`yum install docker docker-compose`

Turn off selinux (it is a security software that isn't necessarily required for something in development)
This fixes issues where the docker container cannot see or write to a mounted folder... after fixing the actual permissions
https://linuxize.com/post/how-to-disable-selinux-on-centos-7/

