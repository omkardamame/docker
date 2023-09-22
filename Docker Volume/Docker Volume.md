There are two types of mounts for docker,
- Volume mount
- Bind mount

Once a volume/dir is attached, changes made, data written will be stored on those volumes and even if the container gets destroyed after usage, the data will be still accessible considering volume gets attached. 
## Volume mount

You can create a docker volume using following command

```bash
docker volume create data_volume
```

Docker volumes are created and stored in following path

```bash
/var/lib/docker/volumes
```

In order to attach docker volume, use the following deprecated but still useful command

This is the command syntax,

```bash
docker run -v <vol_name>:<container_dir> <image>
```

For example,

```bash
docker volume create data_volume
```

```bash
docker run -v data_volume:/var/lib/mysql mysql:latest
```

Even if you don't create a docker volume and still run the command, the docker volume will get created on demand (only works with old -v command).

```
docker run -v data_volume2:/var/lib/mysql mysql:latest
```

## Bind mount

This is the command syntax,

```bash
docker run -v <host_dir>:<container_dir> <image>
```

Example,

```bash
docker run -v /data/mysql:/var/lib/mysql mysql:latest
```

Also, there is newer command syntax for attaching volumes

```bash
docker run \
--mount type=bind,source=data/mysql,target=var/lib/mysql mysql
```

![[docker_volumes.png]]

## Storage Drivers

Docker usages storage drivers to enable to enable layered architecture.

There are the command storage drivers

- AUFS
- ZFS
- BTRFS
- Device Mapper
- Overlay
- Overlay2

These storage drivers will be automatically selected by docker depending on underlying host OS.  For example, in Ubuntu the default storage driver is AUFS. Also these can be manually set by your/organization's needs.