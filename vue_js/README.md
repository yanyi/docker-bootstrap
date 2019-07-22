# Vue.js

## Creating a New Vue.js App

As the Docker image built for the `web` service contains a global
[@vue/cli](https://cli.vuejs.org/) and related dependencies (`Dockerfile`), you
can run the following command to create a new Vue.js app:

```sh
docker-compose run web vue create .
```

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
  - .:/usr/src/vue_js
  - /usr/src/vue_js/node_modules
```
