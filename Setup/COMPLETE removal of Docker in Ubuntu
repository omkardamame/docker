# Uninstalling old versions

If you have already docker installed and some content is present (like containers, volumes), do these steps to remove Docker completely or skip directly to 'Installing using Apt repository' section

## 1. Removing docker images, containers, volumes and configs
Remove all docker images
```
docker rmi $(docker images -a -q)
```

Remove all existed docker containers,

```
docker rm $(docker ps -a -f status=exited -q)
```

Remove all runiing docker contaieners by first stopping them and later removing them,

```
docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)
```

Remove all docker networks

```
docker network prune
```

Remove all unused docker components

```
docker system prune -a
```

## 2. Delete Docker packages
Eradicate docker packages from the system

```
sudo apt-get purge docker-ce docker-ce-cli containerd.io
```

## 3. Deleting the remaining docker files
All docker files will be present in `/var/lib/docker` path
```
sudo rm -rf /var/lib/docker /etc/docker
```

Deleting docker group

```
sudo groupdel docker
```

Deleting docker sockets

```
sudo rm -rf /var/run/docker.sock
```

Deleting anything related to docker-compose(old)

```
sudo rm -rf /usr/local/bin/docker-compose
sudo rm -rf /etc/docker
sudo rm -rf ~/.docker
```

## 4. Cleaning up the unused packages and dependencies

```
sudo apt autoremove
```

References:

https://www.golinuxcloud.com/ubuntu-uninstall-docker/
