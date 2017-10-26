## Base Image to build the container from

FROM ubuntu:16.04
ENV DEBIAN_FRONTEND noninteractive

## System Updates

RUN apt-get -y update
RUn apt-get -y upgrade
RUN apt-get -y update
RUN apt-get install -y sudo
RUN apt-get install -y apt-utils
RUN apt-get install -y build-essential
RUN apt-get -y update


## Dependencies needed

RUN apt-get -y install python3.5
RUN apt-get install -y python3-pip
RUN pip3 install --upgrade pip
RUN apt-get install -y python3-tk
RUN pip3 install matplotlib==2.0.2
RUN pip3 install numpy==1.12.1
RUN pip3 install scipy==0.19.0
RUN pip3 install scikit-learn==0.18.1
RUN pip3 install scikit-image==0.13.0

## Setting the working directory 
WORKDIR /home

## Creating the folders that will be the volumes

RUN mkdir code
RUN mkdir results


## Attaching the code and the results volumes

VOLUME code
VOLUME results

## Running the experiment
CMD python3.5 code/experiment.py