# Python-Docker-Flask
This is a basic python-flask web application in docker.

## Requirements

- [Install Docker](https://docs.docker.com/engine/install/)
- [Install Docker Compose](https://docs.docker.com/compose/install/)

## Prerequisite

Python Flask application code - app.py
Modules required for the application in file - requirements.txt

## Building a Docker Image

1. Generate a Dockerfile inorder to build a docker image. Always keep in mind that this file should be placed inside a specific folder. 

```
$ mkdir appdir

$ cd appdir


$ vim Dockerfile

FROM alpine:3.8                       ------->       ### To create temporary container from the base image ###

RUN mkdir /var/flaskapp               ------->       ### Executes the command to create a directory ###

WORKDIR   /var/flaskapp               ------->       ### Reset the default working directory to /var/flaskapp ###

COPY . .                              ------->       ### Copy the contents from local directory to the default working directory of container ###

RUN apk update && apk add python3     ------->       ### Install python3 ###

RUN pip3 install -r requirements.txt  ------->       ### Install all the modules mentioned in dependency file ###

EXPOSE 5000                           ------->       ### Port publishing ###

CMD ["/usr/bin/python3" , "app.py"]   ------->       ### Default command to be executed when container is created ###
```

2. Create a docker image

```
 $ docker build -t aryamathew/devflaskapp:1 .
```

3. Tag the image

```
 $ docker tag swathikarun/devflaskapp:1 aryamathrew/devflaskapp:latest
```

4. Push the image to dockerhub

```
 $ docker image push swathikarun/devflaskapp:latest
 $ docker image push swathikarun/devflaskapp:1
```
 
## Download the created image from the repository

```
 $ docker image pull aryamathew/devflaskapp:latest
```
 
## Create a container using this image

```
 $ docker container run --name app -d -p 80:5000 aryamathew/devflaskapp:latest
```
 
## Provisioning

1. Clone this repository
```
git clone https://github.com/AryaMathew/Python-Docker-Flask.git
```
2. Switch to the cloned directory
```
cd Python-Docker-Flask
```
3. Start the docker containers using
```
docker-compose up -d
```
4. To stop and remove the containers,networks or volumes associated with this docker, you can use
```
docker-compose down -v
```
 
 ## Result
 
 A web application is created with python-flask in docker.
