ARG NODE_IMAGE=node
ARG NODE_VER=12.6.0

# For local development with docker-compose
FROM ${NODE_IMAGE}:${NODE_VER} AS base

WORKDIR /usr/src/vue_js

RUN yarn global add \
  @vue/cli \
  @vue/cli-service
