## Build the experiment docker container

docker build -t experiment-docker .

## View the new image

docker images | grep experiment

## Check the running containers

docker ps

## Create an asbsolute tail variables

export host_volumes="/home/fyc/Documents/Talks/ComputationalMethods/demos/containers/docker"


## Run the experiment docker container

docker run -it -v $host_volumes/code/:/home/code/ -v $host_volumes/results/:/home/results/ experiment-docker

## Save the container image

docker save experiment-docker > experiment-docker.tar 

## Tag the container image

docker tag experiment-docker palingwende/experiment-docker

## Make sure you are logged in

docker login

## Push your container to dockerhub

docker push palingwende/experiment-docker:latest