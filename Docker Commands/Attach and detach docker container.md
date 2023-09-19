Run a docker images in detached mode (it will give you container ID string)

```bash
sudo docker run -d centos --name container-name-here
```

To attach docker container use following command

```bash
sudo docker attach <container_id/name>
```

If you are stuck in attached docker container, you have to stop the container using another terminal.