## Docker Engine components

Docker engine consist of 3 components
- Docker CLI
- REST API
- Docker Daemon

**Docker Daemon:**
- Manages Docker objects such as images, containers, volumes and networks.

**REST API:**
- It is the API that programs can use to talk to the daemon and provide instructions.

**Docker CLI:**
- Is is used to perform actions such as running a container. stopping a container and so on.
- Uses the REST API to interact with Docker Daemon
- Can be an another system.

```bash
docker -H=<ip_addrs>:2375 run <image>
```

Docker uses namespaces to provide isolations
- Process ID
- Network
- InterProcess
- Mount
- Unix Timesharing

**Process ID**

As there is no hard isolation in Docker, each process can have multiple process ID but cannot be same so the host has for example PID : 5 but in container that PID can be 6.
This way the child system (system present in container) thinks it's independent.

If we have nginx service, on host it will show different process ID but in container it will show different process ID than host. That indicates that all process are in fact running on the same host but separated into their own containers using namespaces.

![[namespace_pid.png]](https://github.com/omkardamame/docker/blob/main/Docker%20Engine/namespace_pid.png)

## cgroups

As Docker engine and host share same resources, by default there is no restriction for resource usage in Docker so a container may use all of available host resources.

cgroups can restrict usage of resources of host.
These are the examples,

```bash
docker run --cpus=.5 ubuntu
```

This will make sure `ubuntu` image won't use more than 50% of CPU at any given time.

```bash
docker run --memory=100m ubuntu
```

This will make sure `ubuntu` image won't use more than 100 MB of memory.
