# Gatsby

## Creating a New Gatsby App

The following command helps you to create a new Gatsby project in your current
working directory (be sure to change the `git config` name and email):

```sh
docker-compose run new \
  sh -c \
  "git config --global user.name REPLACE_ME && \
  git config --global user.email REPLACE_ME && \
  gatsby new temp && \
  cp -aR temp/. . && \
  rmdir temp"
```

1. It uses a `temp` naming for the project, which allows the `git clone` command
   by `gatsby new <project-name>` to work. There is a need to set the Git name
   and email address because the `gatsby new` command includes an initial commit
   automagically.

2. The `rmdir` command will fail because the directory is empty. I did not
   choose to use `rm -rf temp/`. However, do change the command as you see fit.

## Local Development

To start local development, run:

```sh
docker-compose up web
```

### Notes

`yarn install` is added to the Docker Compose `command` in order to install the
dependencies required. This is due to the fact that we ignore `node_modules`
folder when attaching a blank `volume` to the container:

```yaml
volumes:
  - .:/usr/src/gatsby_js
  - /usr/src/gatsby_js/node_modules
```

## Production Image

To build a production Docker image, you can run:

```sh
docker build -t my-awesome-app:latest .
```

It makes use of Docker's multistage build to copy the compiled assets into a
NGINX Alpine image to result in a smaller Docker image.

```sh
docker run --rm -d -p 8080:80 my-awesome-app:latest
```
