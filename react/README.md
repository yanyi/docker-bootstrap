# React

## Creating a New React App

The following command helps you to create a new React project in your current
working directory:

```sh
$ docker-compose run web yarn create react-app temp && \
  mv temp/* temp/.* . && \
  rmdir temp

Creating a new React app in /usr/src/react_js/temp.
...
Done in 142.69s.
```

It uses a `temp` naming for the project and copies all the created files to the
current directory.

### Changing App Name

You might want to change the app name in `package.json`:

```json
{
  "name": "my-awesome-app"
}
```

## Local Development

To start local development, run:

```sh
$ docker-compose up web

Starting react_js_web_1 ... done
Attaching to react_js_web_1
web_1  | yarn install v1.16.0
...
web_1  | You can now view my-awesome-app in the browser.
web_1  |
web_1  |   Local:            http://localhost:3000/
```

### Notes

`yarn install` is added to the Docker Compose `command` in order to install the
dependencies required. This is due to the fact that we ignore `node_modules`
folder when attaching a blank `volume` to the container:

```yaml
volumes:
  - .:/usr/src/react_js
  - /usr/src/react_js/node_modules
```

## Production Image

To build a production Docker image, you can run:

```sh
$ docker build -t my-awesome-app:latest .

Sending build context to Docker daemon  464.4kB
...
Successfully built xxx
Successfully tagged my-awesome-app:latest
```

It makes use of Docker's multistage build to copy the compiled assets into a
NGINX Alpine image to result in a smaller Docker image.

```sh
$ docker run --rm -d -p 8080:80 my-awesome-app:latest

xxx
```
