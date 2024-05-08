# 300 - 3. Create Images defined as Docker file(s)

To create Images defined as Docker file(s), for the ```gateway``` service run:

```
$ cd gateway
$ docker build -f Dockerfile.dev -t agility-game-home-dev:gateway .
$ docker images
REPOSITORY  TAG  IMAGE ID    CREATED   SIZE

```

And for the ```webui``` service run:

```
$ cd webui
$ docker build -f Dockerfile.dev -t agility-game-home-dev:webui .
$ docker images
REPOSITORY  TAG  IMAGE ID    CREATED   SIZE

```

More
