The [**expose**](https://docs.docker.com/engine/reference/builder/#expose) keyword in a Dockerfile tells Docker that a container listens for traffic on the specified port. So, for a container running a web server, you might add this to your Dockerfile: 

`EXPOSE 80`

This tells Docker your webserver will listen on port 80 for TCP connections since TCP is the default. For UDP, specify the protocol after the port. 

`EXPOSE 35/udp`

For more than one port, you can list **EXPOSE** more than once. 

`EXPOSE 80/tcp   EXPOSE 80/udp   EXPOSE 443/tcp   EXPOSE 8081/udp`

While you don't have to specify TCP, it often makes a list of mixed protocol ports easier to read. 

Exposing a port doesn't make it available when you run a container.  To do that, you need to **publish** your ports. Depending on how you want to use the port, you need to map it, too. You can publish your port using -p argurment.