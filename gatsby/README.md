# Gatsby

## Creating a New Gatsby App

The following command helps you to create a new Gatsby project in your current
working directory:

```sh
$ docker-compose run web gatsby new temp && \
  mv temp/* temp/.* . && \
  rmdir temp

info Creating new site from git: https://github.com/gatsbyjs/gatsby-starter-default.git
Cloning into 'temp'...
...
Done in 175.39s.
```

It uses a `temp` naming for the project, which allows the `git clone` command by
`gatsby new <project-name>` to work.

## Local Development

To start local development, run:

```sh
$ docker-compose up web

Starting gatsby_js_web_1 ... done
Attaching to gatsby_js_web_1
web_1  | yarn install v1.16.0
...
You can now view gatsby-starter-default in the browser.
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
