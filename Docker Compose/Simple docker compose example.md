## 1. Intro

Docker compose is nothing but just a tool for defining and running multi-container _Docker_ applications with a simple YAML file.

There are several versions of docker-compose file are present but one should go for `version: "3"` as it is the latest one as of writing this note.

Check docker version by following command

```bash
docker compose version
```

This should output something like this

```bash
Docker Compose version v2.21.0
```

## 2. Architecture of the app

![[arch_voting_app.png]]

The `worker`, `vote` and `result` app are custom made so before starting docker compose, you'll need to either build & push those app to your dockerhub repo and modify the docker compose file accordingly OR have to build the images of them using their respective `Dockerfiles` . The later stuff is pretty easy to implement.

This is just a simple example voting app by which you can understand how docker compose works.

## 3. Git cloning the app

```bash
git clone https://github.com/dockersamples/example-voting-app
```

## 4. Build respective images

Go to `example-voting-app`

**voting-app**

```bash
docker build . -t voting-app
```

**worker-app**

```bash
docker build . -t worker-app
```

**result-app**

```bash
docker build . -t result-app
```

Make sure all above images are present

```bash
root@ubuntu1:~# docker images
REPOSITORY   TAG       IMAGE ID       CREATED             SIZE
result-app   latest    aa5950c37ab5   About an hour ago   266MB
voting-app   latest    2e08113581d8   About an hour ago   145MB
worker-app   latest    e5d274602488   About an hour ago   194MB
```

Write docker compose file

```yaml
version: "3"
services:
  redis:
    image: redis
  db:
    image: postgres:9.4
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
  result:
    image: result-app
    ports:
      - 5001:80
    links:
      - db
  vote:
    image: voting-app
    depends_on:
      - db
      - redis
    ports:
      - 5000:80
    links:
      - redis
  worker:
    image: worker-app
    links:
      - db
      - redis
```

Now just save the file as `docker-compose.yml` and up the docker compose at the same location.

```bash
docker compose up
```

You can see the voting app at `localhost:5000` and results at `localhost:5001`.
Remember, `localhost` is just a placeholder for your VM's or machine's IP.

Note:
- Here, `depends_on` means *db* and *redis* named containers will be created, started before starting *vote* container. Also *vote* will be destroyed before *db* and *redis* containers.
- You can just replace the image names such as `voting-app` with `username/voting-app` if you push the image to dockerhub.

## References:

1. [Example Voting App](https://github.com/dockersamples/example-voting-app](https://github.com/dockersamples/example-voting-app)