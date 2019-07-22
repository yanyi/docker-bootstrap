ARG NODE_IMAGE=node
ARG NODE_VER=12.6.0

# For local development with docker-compose
FROM ${NODE_IMAGE}:${NODE_VER} AS base

WORKDIR /usr/src/gatsby_js

RUN yarn global add \
  gatsby-cli && \
  gatsby telemetry --disable

# For building the image
FROM ${NODE_IMAGE}:${NODE_VER} AS builder

# Copy and do `yarn install` for dependencies and caches them unless there are
# changes in the package.json/yarn.lock.
WORKDIR /usr/src/gatsby_js
COPY package.json yarn.lock ./
RUN yarn install

# Build the application (Gatsby)
COPY gatsby-* ./
COPY src src/
RUN yarn build

# For final resulting image
FROM nginx:1.17.1-alpine

COPY --from=builder /usr/src/gatsby_js/public/ /var/www
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]
