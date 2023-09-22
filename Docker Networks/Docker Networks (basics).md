# Default docker networks:

There are 3 default networks present in Docker

- Bridge
- Host
- none

## Bridge

This is by default network which get attached to all docker containers unless specified. 
Default IP range for this network starts from `172.17.0.0`

To access any of these containers from the outside, we have to map the ports of these containers to ports on host.

```bash
docker run ubuntu
```

## Host

This network provides NO isolation in networking department of container. Any container attached to this container will get host IP and port as it removes any need of port mapping as the web container uses the host's network. This means you cannot run multiple containers on the same host on the same port as the ports are now common to all containers in the host network.

```bash
docker run ubuntu --network=host
```
## none

This is the network where containers is in fully isolation as it cannot use / communicated to host network or even it cannot communicate to other containers; they run in an isolated network.

```bash
docker run ubuntu --network=none
```

![[docker_default_network.png]]

# User-defined networks

```bash
docker network create \
--driver bridge \
--subnet 182.18.0.0/16 \
custom-network
```

![[docker_network_create.png]]

You can check list of docker networks,

```bash
docker network ls
```

Also, you can see network information of docker container using following command,

```bash
docker insepct <container_name>
```

![[docker_network_inspect.png]]

# Embedded DNS

Docker creates a separate namespaces for each container. It uses virtual ethernet pairs to connect containers together. Also it runs its own DNS server.

Docker DNS server runs on `172.0.0.11` IP address. As it maintains a DNS record entries, there is no need to use IP address when connecting two containers; you can just use container names and that would be enough.

![[docker_embedded_dns.png]]