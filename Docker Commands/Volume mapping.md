Mount external directory to docker container

```bash
docker run -v ext-datadir:/internal-datadir mysql
```

This is retain the data on EXTERNAL directory which means even if container gets destroyed, your data remains safe on EXTERNAL directory.

Example:
```bash
sudo docker run -p 8080:8080 -p 50000:50000 -v /root/my-jenkins-data:/var/jenkins_home jenkins/jenkins:latest
```