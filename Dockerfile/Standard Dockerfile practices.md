## Standard Syntax

```Dockerfile
FROM <OS>:<tag>                         #This is a base OS or image
MAINTAINER <your name> <email>          #This will be considered as authour's details
LABEL maintainer="<your name> <email>"
LABEL description="<write here your generic description of dockerfile>"

RUN apt-get update                      #This will install depedencies
RUN apt-get install python

WORKDIR /project                        #Working dir of docker container
COPY . /opt/source-code                 #Source code gets copied into image's location

EXPOSE 3000
ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run   #Running the web server using flask command
```

Make sure you name that file as "Dockerfile" just for simplicity of understanding.

## Building an image

```bash
docker build -f Dockerfile -t omkardamame/my-test-app
```

```bash
docker build -t omkardamame/my-test-app .
```

**Nomenclature of Docker arguments when building an image**

- -t, --tag stringArray              Name and optionally a tag (format: "name:tag")
- -q, --quiet                             Suppress the build output and print image ID on success
- -f, --file string                       Name of the Dockerfile (default: "PATH/Dockerfile")
- --no-cache                            Do not use cache when building the image (reduces image size)

## Naming and tagging an image

To name a local image with ID "0e5574283393" as "fedora/httpd" with the tag "version1.0":

```bash
docker tag 0e5574283393 fedora/httpd:version1.0
```

To name a local image "httpd" as "fedora/httpd" with the tag "version1.0":

```bash
docker tag httpd fedora/httpd:version1.0
```
## Pushing an docker image

```bash
docker push 
```

