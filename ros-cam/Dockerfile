FROM ros:jade-ros-base

ARG DIST=jade
ARG DEBIAN_FRONTEND=noninteractive

# install ros cam related packages
RUN apt-get update && apt-get install -y ros-$DIST-usb-cam
RUN apt-get install -y ros-$DIST-image-view
RUN apt-get install -y ros-$DIST-web-video-server
RUN apt-get install -y streamer

RUN mkdir /roslaunch
WORKDIR /roslaunch

CMD ["roslaunch","usb_cam","usb_cam-test.launch"]
