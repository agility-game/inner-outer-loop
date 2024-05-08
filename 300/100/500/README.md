# 500 - 5. Run Containers / Compose App

Now that we have defined the services in the docker-compose files, we can run the services as follows:

First create any required networks for ```development```:

```
$ docker network create -d gateway-dev
```

Next start the services:

```
$ docker-compose --file docker-compose.dev.yml --project-name agility-game-home-dev up --build -d 
```

Then, create any required networks for ```production```:

```
$ docker network create -d gateway-prod
```

For running the services in ```production``` execute:

```
$ docker-compose --file docker-compose.prod.yml --project-name agility-game-home-prod up --build -d 
```

The above command will start all service contained in the docker-compose file (i.e. ```gateway``` and ```webui```).
