If you pull an image without specifying registry, docker will always pull from `docker.io` registry.
Google uses `gcr.io` as their own registry.

# Create your own local registry

Before creating the registry, make sure to login into docker, otherwise you can't access it.

You'll need to pull `registry:2` first

```bash
docker pull registry:2
```

Give a name to your registry, assign a port and make sure to make it restart automatically to ensure its availability.

```bash
docker run -d --name my-registry -p 5000:5000 --restart=always registry:2
```

Your registry will be available at `localhost:5000` or you can just assign IP/FQDN instead of localhost
# Docker Tag

Before pushing any image, you'll have to tag the image

```bash
docker image tag <image:tag> <username/image_name_you_want:tag>
```

You can also use image ID as tag to push it.

```bash
docker image tag httpd:latest omkardamame/httpd:latest
```

OR

```bash
docker image tag httpd:latest docker.io/omkardamame/httpd:latest
```
# Docker push

After tagging the image, you can push it.

```bash
docker push <registry/username/target-tagged-image>
```

```bash
docker push omkardamame/httpd:latest
```



