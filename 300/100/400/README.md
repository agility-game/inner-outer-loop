# 400 - 4. Define Services by writing Docker-Compose file(s)

The ```docker-compose.yml``` file (or other name used) lets you define a set of related **services** to be deployed as a composed application with deployment commands. It also configures its dependency relations and run-time configuration.

We configure our Docker containers by means of a so-called ```.env``` file.

For example:

```
UNIQUE_NAMESPACE=agility-game-home
IMAGE_REPOSITORY=registry.hub.docker.com
IMAGE_REPOSITORY_DIVISION=/
PROXY_USER=
PROXY_PASSWORD=
PROXY_FQDN=
PROXY_PORT=
```
.env

Note: If not behind a (corporate) proxy, the values for the proxy entries should be left blank.

```
version: "3.7"

# See https://stackoverflow.com/questions/29261811/use-docker-compose-env-variable-in-dockerbuild-file
services:

  webui:
    build:
      context: ./webui
      dockerfile: Dockerfile.dev
      args: # from env_file
        IMAGE_REPOSITORY: ${IMAGE_REPOSITORY}
        IMAGE_REPOSITORY_DIVISION: ${IMAGE_REPOSITORY_DIVISION}
        PROXY_USER: ${PROXY_USER}
        PROXY_PASSWORD: ${PROXY_PASSWORD}
        PROXY_FQDN: ${PROXY_FQDN}
        PROXY_PORT: ${PROXY_PORT}
    env_file:
      - .env
    container_name: ${UNIQUE_NAMESPACE}-webui-dev
    privileged: true    
    security_opt:
      - no-new-privileges:true      
    ports:
      - "8081:3001"
    volumes:
      - ./webui:/app
      - /app/node_modules
    environment:
      - CHOKIDAR_USEPULLING=true
    networks:
      - gateway-dev      

  gateway:
    build:
      context: ./gateway
      dockerfile: Dockerfile.dev
      args: # from env_file
        IMAGE_REPOSITORY: ${IMAGE_REPOSITORY}
        PROXY_USER: ${PROXY_USER}
        PROXY_PASSWORD: ${PROXY_PASSWORD}
        PROXY_FQDN: ${PROXY_FQDN}
        PROXY_PORT: ${PROXY_PORT}
    env_file:
      - .env
    container_name: ${UNIQUE_NAMESPACE}-gateway-dev
    depends_on:
      - webui    
    privileged: true    
    security_opt:
      - no-new-privileges:true
    restart: unless-stopped     
    ports:
      - "8080:80"
    volumes:
      - ./gateway:/app
      - /app/node_modules
    environment:
      - CHOKIDAR_USEPULLING=true
    networks:
      - default
      - gateway-dev
    external_links:
      - agility-game-microservices-webui-dev
      - agility-game-company-purpose-dev

# see https://stackoverflow.com/questions/45255066/create-networks-automatically-in-docker-compose
networks:
  gateway-dev:
    external: true
    name: gateway-dev
```
docker-compose.dev

```
version: "3.7"

# See https://stackoverflow.com/questions/29261811/use-docker-compose-env-variable-in-dockerbuild-file
services:
  webui:
    build:
      context: ./webui
      dockerfile: Dockerfile.prod
      args: # from env_file
        IMAGE_REPOSITORY: ${IMAGE_REPOSITORY}
        IMAGE_REPOSITORY_DIVISION: ${IMAGE_REPOSITORY_DIVISION}
        PROXY_USER: ${PROXY_USER}
        PROXY_PASSWORD: ${PROXY_PASSWORD}
        PROXY_FQDN: ${PROXY_FQDN}
        PROXY_PORT: ${PROXY_PORT}
    env_file:
      - .env      
    container_name: ${UNIQUE_NAMESPACE}-webui-prod
    privileged: true    
    security_opt:
      - no-new-privileges:true      
    ports:
      - "9094:3001"
    networks:
      - gateway-prod      

  gateway:
    build:
      context: ./gateway
      dockerfile: Dockerfile.prod
      args: # from env_file
        IMAGE_REPOSITORY: ${IMAGE_REPOSITORY}
        PROXY_USER: ${PROXY_USER}
        PROXY_PASSWORD: ${PROXY_PASSWORD}
        PROXY_FQDN: ${PROXY_FQDN}
        PROXY_PORT: ${PROXY_PORT}
    env_file:
      - .env      
    container_name: ${UNIQUE_NAMESPACE}-gateway-prod
    depends_on:
      - webui    
    privileged: true    
    security_opt:
      - no-new-privileges:true      
    restart: unless-stopped
    ports:
      - "80:80"  
    networks:
      - default
      - gateway-prod
    external_links:
      - agility-game-microservices-webui-prod
      - agility-game-company-purpose-prod

# see https://stackoverflow.com/questions/45255066/create-networks-automatically-in-docker-compose
networks:
  gateway-prod:
    external: true
    name: gateway-prod
```
docker-compose.prod

More
