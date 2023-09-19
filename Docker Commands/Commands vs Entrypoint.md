Standard syntax for writing commands

![[Pasted image 20230916024729.png]]

**CMD** command is a hardcoded command in a dockerfile.
If we give a command with parameter, it will override the existing command's parameter.
For example,

```bash
docker run ubuntu-sleeper sleep 10
```

**ENTRYPOINT** is command that waits for input from user when starting a container.
For example

```bash
docker run ubuntu-sleeper 10
```

This will run the image in container that run the command "sleep 10".
If we don't give a parameters, it will throw an error.

![img](docker/Docker Commands/Pasted image 20230916025821.png)

## Running container with default startup command without giving a parameter

If we want to don't give a parameter but want to run that command with some default parameter, here we can do this.

```dockerfile
FROM ubuntu

ENTRYPOINT ["sleep"]

CMD ["5"]
```

If we run this command

```bash
docker run ubuntu-sleeper 10
```

It will run the command for 10 seconds but if we run this command

```bash
docker run ubuntu-sleeper
```

It will run the command with 5 seconds.


## Overriding ENTRYPOINT beforehand

```bash
docker run --entrypoint dance ubuntu-sleeper 69
```

This will override existing sleep for 5 seconds command with that dancing one.

