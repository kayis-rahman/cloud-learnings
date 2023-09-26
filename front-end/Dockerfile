FROM node:20-alpine3.17 AS builder
WORKDIR src/app

COPY . .
RUN yarn install
RUN export NODE_OPTIONS=--openssl-legacy-provider && yarn build


# Serve Application using Nginx Server
FROM nginx:alpine
COPY --from=builder src/app/dist/front-end/ /usr/share/nginx/html
EXPOSE 80
