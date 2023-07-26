# syntax=docker/dockerfile:1
FROM node:18-alpine as build
ADD package.json /tmp/package.json
RUN cd /tmp && npm install
RUN mkdir -p /opt/app && cp -a /tmp/node_modules /opt/app/
WORKDIR /opt/app
COPY . .
RUN npm run build

FROM nginx as deployment
COPY --from=build /opt/app/build /usr/share/nginx/html