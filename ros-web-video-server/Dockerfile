FROM ros:jade-ros-core

ARG DIST=jade
ARG DEBIAN_FRONTEND=noninteractive

# install ros cam related packages
RUN apt-get update && apt-get install -y ros-$DIST-web-video-server

CMD ["rosrun","web_video_server", "web_video_server"]
