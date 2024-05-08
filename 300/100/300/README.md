# 300 - 3. Create Images defined as Docker file(s)

To create Images defined as Docker file(s), for the ```gateway``` service for ```development``` run:

=== RUN BELOW COMMAND FROM WITHIN GITPOD, BUT NOT WITHIN THE CONTAINER ===

```
gitpod /workspace/home/dev (main) $ cd ../gateway
gitpod /workspace/home/gateway (main) $ docker build -f Dockerfile.dev -t agility-game-home-dev:gateway .
[+] Building 6.0s (5/5) FINISHED                                                                                                    docker:default
 => [internal] load build definition from Dockerfile.dev                                                                                      0.0s
 => => transferring dockerfile: 598B                                                                                                          0.0s
 => [internal] load metadata for docker.io/library/node:13.12.0-alpine                                                                        2.2s
 => [internal] load .dockerignore                                                                                                             0.0s
 => => transferring context: 2B                                                                                                               0.0s
 => [1/1] FROM docker.io/library/node:13.12.0-alpine@sha256:cc85e728fab3827ada20a181ba280cae1f8b625f256e2c86b9094d9bfe834766                  3.7s
 => => resolve docker.io/library/node:13.12.0-alpine@sha256:cc85e728fab3827ada20a181ba280cae1f8b625f256e2c86b9094d9bfe834766                  0.0s
 => => sha256:cc85e728fab3827ada20a181ba280cae1f8b625f256e2c86b9094d9bfe834766 1.19kB / 1.19kB                                                0.0s
 => => sha256:ed06820d0fb6f4711e0a6f50c9f147fb2596399866319e1bb3b0a52393c5615f 1.16kB / 1.16kB                                                0.0s
 => => sha256:483343d6c5f5d658963b7c16e4299247f765bef4025012457ee105481ea1afc1 6.77kB / 6.77kB                                                0.0s
 => => sha256:aad63a9339440e7c3e1fff2b988991b9bfb81280042fa7f39a5e327023056819 2.80MB / 2.80MB                                                0.2s
 => => sha256:a00bd932208e2de29cd2b7e0bab954325913d146401effb482fff3d8775aaaeb 35.29MB / 35.29MB                                              1.0s
 => => sha256:c57f2c59b93778192e60e0e213949630f9ad30324736bbb0a71e12adf8a16d46 2.24MB / 2.24MB                                                0.4s
 => => extracting sha256:aad63a9339440e7c3e1fff2b988991b9bfb81280042fa7f39a5e327023056819                                                     0.1s
 => => sha256:f3446470f297e51c1e27f90f7ae9a94f1ee7b6c8e529aec83aa1a04ad70531c0 284B / 284B                                                    0.3s
 => => extracting sha256:a00bd932208e2de29cd2b7e0bab954325913d146401effb482fff3d8775aaaeb                                                     2.1s
 => => extracting sha256:c57f2c59b93778192e60e0e213949630f9ad30324736bbb0a71e12adf8a16d46                                                     0.1s
 => => extracting sha256:f3446470f297e51c1e27f90f7ae9a94f1ee7b6c8e529aec83aa1a04ad70531c0                                                     0.0s
 => exporting to image                                                                                                                        0.0s
 => => exporting layers                                                                                                                       0.0s
 => => writing image sha256:17b41f6beae346d2985b52b8857702f970330da7a58f97cc96d30df51ada721f                                                  0.0s
 => => naming to docker.io/library/agility-game-home-dev:gateway                                                                              0.0s
gitpod /workspace/home/gateway (main) $ docker images
REPOSITORY              TAG       IMAGE ID       CREATED         SIZE
node                    19        9b96288651e9   11 months ago   997MB
agility-game-home-dev   gateway   17b41f6beae3   4 years ago     114MB
gitpod /workspace/home/gateway (main) $ 
```

And for the ```webui``` service for ```development``` run:

```
gitpod /workspace/home (main) $ cd webui
gitpod /workspace/home/webui (main) $ docker build -f Dockerfile.dev -t agility-game-home-dev:webui .
[+] Building 0.4s (5/5) FINISHED                                                                                                    docker:default
 => [internal] load build definition from Dockerfile.dev                                                                                      0.0s
 => => transferring dockerfile: 598B                                                                                                          0.0s
 => [internal] load metadata for docker.io/library/node:13.12.0-alpine                                                                        0.4s
 => [internal] load .dockerignore                                                                                                             0.0s
 => => transferring context: 2B                                                                                                               0.0s
 => CACHED [1/1] FROM docker.io/library/node:13.12.0-alpine@sha256:cc85e728fab3827ada20a181ba280cae1f8b625f256e2c86b9094d9bfe834766           0.0s
 => exporting to image                                                                                                                        0.0s
 => => exporting layers                                                                                                                       0.0s
 => => writing image sha256:17b41f6beae346d2985b52b8857702f970330da7a58f97cc96d30df51ada721f                                                  0.0s
 => => naming to docker.io/library/agility-game-home-dev:webui                                                                                0.0s
gitpod /workspace/home/webui (main) $ docker images
REPOSITORY              TAG       IMAGE ID       CREATED         SIZE
node                    19        9b96288651e9   11 months ago   997MB
agility-game-home-dev   gateway   17b41f6beae3   4 years ago     114MB
agility-game-home-dev   webui     17b41f6beae3   4 years ago     114MB
```

More
