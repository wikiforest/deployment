FROM nginx:latest

ARG DOCKER_ENV

WORKDIR /etc/nginx

COPY ./nginx.conf ./nginx.conf
COPY ./templates ./templates
COPY ./cert/${DOCKER_ENV} /etc/nginx/cert
