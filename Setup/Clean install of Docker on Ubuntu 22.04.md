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

Run the following command to uninstall all conflicting packages:

```bash
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt remove $pkg; done
```

# Installing using Apt repository

## 1. Set up Docker's Apt repository

### Add Docker's official GPG key:

```bash
sudo apt-get update
```

```bash
sudo apt-get install ca-certificates curl gnupg
```

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

### Add the repository to Apt sources:

```bash
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt-get update
```

## 2. Installing the Docker packages

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 3. Verify that the Docker Engine installation is successful by running the `hello-world` image.

```bash
sudo docker run hello-world
```

This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

You have now successfully installed and started Docker Engine.
