FROM ros:jade-ros-base

ARG DIST=jade
ARG DEBIAN_FRONTEND=noninteractive

# install ros cam related packages
RUN apt-get update && apt-get install -y ros-$DIST-web-video-server

