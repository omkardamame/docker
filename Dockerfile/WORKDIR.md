If the `WORKDIR` command is not written in the Dockerfile, it will automatically be created by the Docker compiler. Hence, it can be said that the command performs `mkdir` and `cd` implicitly.

If the `project` directory does not exist, it will be created. The `RUN` command will be executed inside `project`.

Any `RUN`, `CMD`, `ADD`, `COPY`, or `ENTRYPOINT` command will be executed in the specified working directory.