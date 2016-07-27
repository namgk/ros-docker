FROM ros:jade-ros-core

ARG DIST=jade
ARG DEBIAN_FRONTEND=noninteractive

# install ros cam related packages
RUN apt-get update && apt-get install -y ros-$DIST-usb-cam

RUN mkdir /roslaunch
ADD *.launch /roslaunch/

WORKDIR /roslaunch

CMD ["roslaunch","usb_cam.launch"]
