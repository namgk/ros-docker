FROM ros:jade-ros-core

ARG DIST=jade
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y ros-$DIST-cv-bridge

RUN mkdir /catkin_ws
WORKDIR /catkin_ws

