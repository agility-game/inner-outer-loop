# 200 - 2. Write Docker file(s)

You need a Dockerfile for each custom image you want to build; you also need a **Dockerfile** for each container to be deployed, whether you deploy automatically from your IDE or manually using the Docker CLI (```docker run``` and ```docker-compose``` commands). 

- If your application contains a single custom service, you need a single Dockerfile. 
- If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.

The Dockerfile is placed in the ```root / service``` folder of your application or service. It contains the commands that tell Docker how to set up and run your application or service in a container. You can manually create a Dockerfile in code and add it to your project along with your dependencies.

For example, to host our **gateway** service, we add a Dockerfile to the directory ```/gateway/```. And to host our **webui** service, we add a Dockerfile to the directory ```/webui/```.

Note that for ```development``` our Dockerfile is named **Dockerfile.dev**, whereas for ```production``` our Dockerfile is named **Dockerfile.prod**. It contains the commands that tell Docker how to set up and run your application or service in a container. You can manually create a Dockerfile in code and add it to your project along with your dependencies.

For example:

```
ARG IMAGE_REPOSITORY
ARG IMAGE_REPOSITORY_DIVISION
# development environment: pull official base image for node development
FROM ${IMAGE_REPOSITORY}${IMAGE_REPOSITORY_DIVISION}node:13.12.0-alpine as build

# See https://stackoverflow.com/questions/29261811/use-docker-compose-env-variable-in-dockerbuild-file
ARG PROXY_USER
ARG PROXY_PASSWORD
ARG PROXY_FQDN
ARG PROXY_PORT

ENV HTTP_PROXY="http://${PROXY_USER}:${PROXY_PASSWORD}@${PROXY_FQDN}:${PROXY_PORT}"
ENV HTTPS_PROXY="http://${PROXY_USER}:${PROXY_PASSWORD}@${PROXY_FQDN}:${PROXY_PORT}"

# More ...
```
gateway/Dockerfile.dev


```
ARG IMAGE_REPOSITORY
ARG IMAGE_REPOSITORY_DIVISION
# development environment: pull official base image for node development
FROM ${IMAGE_REPOSITORY}${IMAGE_REPOSITORY_DIVISION}node:13.12.0-alpine as build

# See https://stackoverflow.com/questions/29261811/use-docker-compose-env-variable-in-dockerbuild-file
ARG PROXY_USER
ARG PROXY_PASSWORD
ARG PROXY_FQDN
ARG PROXY_PORT

ENV HTTP_PROXY="http://${PROXY_USER}:${PROXY_PASSWORD}@${PROXY_FQDN}:${PROXY_PORT}"
ENV HTTPS_PROXY="http://${PROXY_USER}:${PROXY_PASSWORD}@${PROXY_FQDN}:${PROXY_PORT}"

# More ...
```
gateway/Dockerfile.prod
