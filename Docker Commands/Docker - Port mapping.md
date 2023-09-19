For starter, download following image

```bash
sudo docker run kodekloud/webapp
```

Attach or change the port to access the site present in container

```bash
sudo docker run -p <accessible port>:<containerside port> 
sudo docker run -it -p 80:5000 kodekloud/webapp
```

Also, we can run multiple containers with different ports

```bash
sudo docker run -p 80:5000 kodekloud/webapp
sudo docker run -p 81:5000 kodekloud/webapp
sudo docker run -p 82:5000 kodekloud/webapp
```

