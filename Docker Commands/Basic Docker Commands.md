Pull a docker images (it doesn't run automatically)

```bash
sudo docker pull centos
```

Run a docker images

```bash
sudo docker run centos
```

Run a docker images in interactive mode

```bash
sudo docker run -it centos
```

Check all docker images available locally

```bash
sudo docker images
```

Check running docker containers

```bash
sudo docker ps
```

Check all docker containers including stopped containers

```bash
sudo docker ps -a
```

Stop a docker container (it can be multiple) (it will give exit code 137 which means forcefully exited)

```bash
sudo docker stop <container name or id>
sudo docker stop nice_bund
sudo docker stop 69420
```

Remove a docker container (it can be multiple)

```bash
sudo docker rm <container id or name>
sudo docker rm nice_bund
sudo docker run 69420
```

Remove docker images (it can be multiple)

```bash
sudo docker rmi <repository/image name>:<tag which might be latest or a version>
sudo docker rmi centos    #this will always remove the "latest" tagged image
sudo docker rmi centos:1.2.3.4
```

