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
- first, connect the ethernet cable to your computer.
- now, you should be able to control the robot!

### Controller Settings
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/fefb2f5c-cb42-427b-a20d-c7e0fbebe481" width="250">
- Here, click "program the robot"
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/fa040d3a-7588-4d67-827b-b6513a80d488" width="250">
-  select load program
-  <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/4fa95cac-9f5f-4848-b318-d1e9acbfac6b" width="250">
- select ros_driver.urp
- now you should give your computers ip to the robot. go to installation - external control. Change the host ıp part. You can the ```ifconfig``` command to see your ip. Also you will need the robots ip too. You can check the robots ip by clicking the "UR" symbol on top left.
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/e6082ef2-543f-43d7-bfb8-5c9efa1e0c4c" width="250">
- now go to 'program' section, you will see the play button at the buttom. Click that. Now you should see the screen below:
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/03fe8d37-4b37-4db2-af0c-603ea2fbbe0f" width="250">
- click the button that says start two times. Then click OK. Now you should be back at the program section.
- Now, pressing the start button at the button of the "program" section will start the robot. There is also a stop button there to stop the robot. Make sure that you are not using the robot at full speed! At the program section, there is also a slider that controls the speed. You can lower that when you are running your script.
- After you are done, first press the stop button. Then click "move" above.
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/16261e2f-72d0-4a5a-af6b-3c62b62c55f0" width="250">
- This page helps you to move the robot. We will use it to move to robot to its inital position. Click home.
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/143467fa-6a0f-48d6-a434-c56c7ff92feb" width="250">
- Here click auto to move the robot to its initial position. Always move the robot to its initial position before closing the controller.
- After that, click file to and close the program to go to the initial screen. Then you can close the controller using the button on the controller.







### Problems that you might encounter
