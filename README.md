# Docker Bootstrap

Docker Bootstrap enables a developer to make use of Docker to bootstrap
applications with Dockerfiles and `docker-compose` to keep their local computer
clean.

Generally, the concept is using a Dockerfile to create a Docker image with the
minimum amount of dependencies needed to bootstrap a new application for local
development.

After building the Docker image, the Docker image can then be used for using
with `docker-compose` to `run` commands or even bring up a service (using `up`).
