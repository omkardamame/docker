It is very difficult to deploy and manage multiple docker containers for production and organization manually so in this case there is a need for container orchestration. In this case, there is docker swarm.

With Docker Swarm, you can combine multiple docker machines together into a single cluster. The docker swarm will take care of distributing your services or your application instances into separate hosts for high availability and for load balancing across different systems and hardware.

## **Setup of Docker Swarm**

You'll need to have at least two or more hosts with Docker installed in them. Then you must designate one host to be the manager or the master or the swarm manager and others as slave or worker.

Example for initializing docker swarm,

```bash
docker swarm init --advertise-addr <ip_of_swarm_manager>
```

It will show a command with join token in it.

To add a worker to this swarm, run the following command

```bash
docker swarm join --token wasdawsd-wadasdaw <ip_of_swarm_manager>:2377
```

## Docker service

To run your application or service in docker swarm, use following command..

```bash
docker service create --replicas=3 my-app
```

Here considering you have 3 hosts, we have taken replicas as 3. This means each worker will have one instance of your application running on them.

Make sure to **RUN DOCKER SERVICE COMMAND ONLY ON MANAGER NODE!**

You can use other options as -p, --network as you normally use docker run command.