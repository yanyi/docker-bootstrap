# Vue.js

## Creating a New Vue.js App

As the Docker image built for the `web` service contains a global
[@vue/cli](https://cli.vuejs.org/) and related dependencies (`Dockerfile`), you
can run the following command to create a new Vue.js app:

```sh
$ docker-compose run web vue create .

Vue CLI v3.9.3
? Generate project in current directory? (Y/n)
...
```

## Local Development

To start local development, run:

```sh
$ docker-compose up web

Creating vue_js_web_1 ... done
Attaching to vue_js_web_1
web_1  | yarn install v1.16.0
...
web_1  |   App running at:
web_1  |   - Local:   http://localhost:8080/
```

### Notes

`yarn install` is added to the Docker Compose `command` in order to install the
dependencies required. This is due to the fact that we ignore `node_modules`
folder when attaching a blank `volume` to the container:

```yaml
volumes:
  - .:/usr/src/vue_js
  - /usr/src/vue_js/node_modules
```
