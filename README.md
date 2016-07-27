# ros-docker
Personal docker images for ros cam, ros web video server

Available at https://hub.docker.com/r/nhong/

##How to run:

1. Create a new network for ros so that ros nodes can reach each other via their container names

sudo docker network create -d bridge ros

2. Run the master

docker run -it --name roscore --net=ros ros:jade-ros-core roscore

3. Run the camera node

docker run -it --name roscam --net=ros -e ROS_MASTER_URI=http://roscore:11311 -e ROS_HOSTNAME=roscam -v /dev/video0:/dev/video0 --privileged nhong/ros:usbcam

4. Run the web video stream node

docker run -it --name rosweb --net=ros -e ROS_MASTER_URI=http://roscore:11311 -e ROS_HOSTNAME=rosweb -p 8888:8080 nhong/ros:webvideo

5. See the camera on the browser at http://localhost:8888

##Explanation
Ros nodes communicate with each other via direct TCP so they need to see each other directly using ip/hostname and port.

--name roscam: enable other containers to reach this container via hostname "roscam", this won't work in Docker's default bridge so step 1 is required.

-e ROS_HOSTNAME=roscam: tells the node to advertise the reachable hostname to other nodes.

-e ROS_MASTER_URI=http://roscore:11311: tells the node where is the ros master

-v /dev/video0:/dev/video0 AND --privileged: allow container to access webcam attached at /dev/video0
