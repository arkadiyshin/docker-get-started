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

**build -t\[name:tag\] \[path to Dockerfile\]**
```
docker build .
```

## STEP 4
run custom container

**docker run -p \[local port\]:\[expoused port\] -d -name -rm \[image_name or image_id\]**
*-p parametr matches local port and expoused port*
*-rm parametr deletes container after stopping*
*-d parametr runs container in detached mode (attached mode by the default)*

stop a running container

**docker stop \[container_name or container_id\]**

run a stopping container

**docker start -a \[container_name or container_id\]**
*-a parametr runs container in attached mode (detached mode by the default)*

attach running container

**docker attach \[container_name or container_id\]**

## STEP 5
delete images and containers

**docker rmi \[image_name or image_id\]**
**docker rm \[container_name or container_id]**

delete all images 

**docker image prune**

## STEP 6
share images

create new repository in dockerhub

rename your local repository with dockerhub name

**docker tag \[local-image:tagname\] \[new-repo:tagname\]**

push your local image to dockerhub

**docker push \[new-repo:tagname\]**

for pushing into dockerhub you need to authorize

**docker login**
*you will stay loged in*

for logout

**docker logout**
