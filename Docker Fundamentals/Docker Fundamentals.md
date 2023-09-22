## Docker file system

Docker stores it's files in following directory

```bash
/var/lib/docker
```

## Layered Architecture

Docker builds image in following sequence

- Layer 1: Base OS layer
- Layer 2: Changes in apt/yum packages
- Layer 3: Changes in pip/other packages
- Layer 4: Source code
- Layer 5: Updating CMD, entrypoint and commands
- Layer 6: Container Layer

Each layer are its own size and is reflected when building the image.

First three layers are usually get cached and reused wherever possible to reduce time and space usage.

Once an image is built, it becomes READ-ONLY. If you want to make changes, you'll have to build a new image.

Layer 6 is the READ-WRITE image which gets build after running a docker container from a image.
This is temporary layer as it stores logs, any data changes. The life of this layer is only as long as the container alive. When container is destroyed the container and all the Layer 6 gets destroyed.

![[docker_layers.png]]


