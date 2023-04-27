# DOCKER CUSTOM INSTRUCTIONS

## STEP 1
find required for the project docker image

**run \[image_name\]**: searches for a local image by name, if not found, downloads from dockerhub and then runs
```
docker run node
 
# interactive mode
docker run -it node 
```

*see running containers*
```
docker ps
```

*see all the containers*
```
docker ps -a
```

## STEP 2
create Dockerfile in the root of the project.

*Simple sample docker file*
```
FROM node
 
# change working directory like cd command in terminal
WORKDIR /app 

COPY package.json /app

# run the command for installing dependencies
RUN npm install

# copy all files from project directory to the container
COPY . /app 
  
# [optional] information about shared port from container
EXPOSE 80
 
# run the command to runnig our programm
# the difference from the RUN command is that 
# CMD is executed only after the container has been built and started
CMD ["npm", "start"]
```
## STEP 3
create our own custom image

**build [path to Dockerfile]**
```
docker build .
```

## STEP 4

run custom container

**docker run -p [local port]:[expoused port]  [image_name or image_id]**

stop a running container

**docker stop [container_name or container_id]**

run a stopping container

**docker start [container_name or container_id]**

run starting in attach mode by default, start in detach mode. 
Use -d parametr to running in detach mode.
Use -a parametr to running in attach mode.
For attaching running container use attach command

**docker attach [container_name or container_id]**
