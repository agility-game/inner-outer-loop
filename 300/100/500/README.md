# 500 - 5. Run Containers / Compose App

Now that we have defined the services in the docker-compose files, we can run the services as follows:

First create any required networks for ```development```:

```
$ docker network create gateway-dev
```

Next start the services:

```
gitpod /workspace/home (main) $ docker-compose --file docker-compose.dev.yml --project-name agility-game-home-dev up --build -d
[+] Building 0.6s (8/8) FINISHED                                                                                                   docker:default
 => [webui internal] load build definition from Dockerfile.dev                                                                               0.0s
 => => transferring dockerfile: 598B                                                                                                         0.0s
 => [gateway internal] load metadata for docker.io/library/node:13.12.0-alpine                                                               0.5s
 => [webui internal] load .dockerignore                                                                                                      0.0s
 => => transferring context: 2B                                                                                                              0.0s
 => CACHED [gateway 1/1] FROM docker.io/library/node:13.12.0-alpine@sha256:cc85e728fab3827ada20a181ba280cae1f8b625f256e2c86b9094d9bfe834766  0.0s
 => [webui] exporting to image                                                                                                               0.0s
 => => exporting layers                                                                                                                      0.0s
 => => writing image sha256:6a464b6c3674c5bf8f9b6d1f0a7246d4fbd9a78487ff66135b2e9b74dc3d9902                                                 0.0s
 => => naming to docker.io/library/agility-game-home-dev-webui                                                                               0.0s
 => [gateway internal] load build definition from Dockerfile.dev                                                                             0.0s
 => => transferring dockerfile: 598B                                                                                                         0.0s
 => [gateway internal] load .dockerignore                                                                                                    0.0s
 => => transferring context: 2B                                                                                                              0.0s
 => [gateway] exporting to image                                                                                                             0.0s
 => => exporting layers                                                                                                                      0.0s
 => => writing image sha256:0ffbc559f1005bcbaee4d4f98ee873c262d039a37617d3b7efa8e57438a1632b                                                 0.0s
 => => naming to docker.io/library/agility-game-home-dev-gateway                                                                             0.0s
[+] Running 2/2
 ✔ Container agility-game-home-webui-dev    Started                                                                                          0.0s 
 ✔ Container agility-game-home-gateway-dev  Started                                                                                          0.0s 
gitpod /workspace/home (main) $ 
```

Then, create any required networks for ```production```:

```
$ docker network create gateway-prod
```

For running the services in ```production``` execute:

```
$ docker-compose --file docker-compose.prod.yml --project-name agility-game-home-prod up --build -d 
```

The above command will start all service contained in the docker-compose file (i.e. ```gateway``` and ```webui```).
