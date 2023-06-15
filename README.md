# ur10_setup
- This document covers how to control the UR10 robot. It covers the packages and applications that you need to download and shows you to run a simple script.

### Ros Noetic
- The first thing that you will need to install is ROS Noetic. The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications.
- Right now, ros noetic is only suppoted for ubuntu 20.06. So it is easier to install ubuntu than trying the experimental versions of ros for windows.
- You can check https://www.youtube.com/watch?v=sl_uR4rkPz4 to use ubuntu as a dual boot configuration with windows 10.
- you can install ros noetic following the instructions here: http://wiki.ros.org/noetic/Installation/Ubuntu
### Additional packages
- After installing ubuntu and ros, you clone the following repo: https://github.com/ocg2347/UR10_dockerized. This repo contains some scripts that you can try to run. You can use visual studio code for ubuntu :https://code.visualstudio.com/docs/setup/linux
- After cloning the repo, you can build the docker image using the following commnad: ``` docker build PATH -t "some tag" ```
-  PATH is the path to the repo that you downloaded. Ypu can check your docker images using ``` docker images ```
- There are few additonal packages that you need to install : You can check these links to install them.
- https://github.com/cambel/ur_ikfast
- https://github.com/Nishida-Lab/robotiq_3f_ros_pkg
- http://wiki.ros.org/robotiq/Tutorials/Control%20of%20a%203-Finger%20Gripper%20using%20the%20Modbus%20TCP%20Protocol
- After downloading these, you may need to remove the file "devel" from catkin_ws and run ```catkin build```.
- Also you need to install libraries such as Numpy and Scipy. ıf you see an error like "Rotation cannot be expressed as matrix" check your Scipy version.
### Running the Script
- 







### Problems that you might encounter
