# ur10_setup
- This document covers how to control the UR10 robot. It covers the packages and applications that you need to download and shows you to run a simple script.

### Ros Noetic
- The first thing that you will need to install is ROS Noetic. The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications.
- Right now, ros noetic is only supported for ubuntu 20.06. So it is easier to install ubuntu than trying the experimental versions of ros for windows.
- You can check https://www.youtube.com/watch?v=sl_uR4rkPz4 to use ubuntu as a dual boot configuration with windows 10.
- you can install ros noetic following the instructions here: http://wiki.ros.org/noetic/Installation/Ubuntu
### Additional packages
- After installing ubuntu and ros, you can clone the following repo: https://github.com/ocg2347/UR10_dockerized. This repo contains some scripts that you can try to run. You can use visual studio code for ubuntu :https://code.visualstudio.com/docs/setup/linux
- After cloning the repo, you can build the docker image using the following command: ``` docker build PATH -t "some tag" ```
-  PATH is the path to the repo that you downloaded. You can check your docker images using ``` docker images ```
- There are few additonal packages that you need to install : You can check these links to install them.
- https://github.com/cambel/ur_ikfast
- https://github.com/Nishida-Lab/robotiq_3f_ros_pkg
- http://wiki.ros.org/robotiq/Tutorials/Control%20of%20a%203-Finger%20Gripper%20using%20the%20Modbus%20TCP%20Protocol
- After downloading these, you may need to run ```catkin build``` to build the workspace again. In catkin_ws remove the "devel" file to build the workspace again.
- Also you need to install libraries such as NumPy and Scipy. If you see an error like "Rotation cannot be expressed as matrix" check your Scipy version.

### Controller Settings and Running Scripts
- first, connect the ethernet cable to your computer and turn on the controller.
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/fefb2f5c-cb42-427b-a20d-c7e0fbebe481" width="250">
- Here, click "program the robot"
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/fa040d3a-7588-4d67-827b-b6513a80d488" width="250">
-  select load program
-  <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/4fa95cac-9f5f-4848-b318-d1e9acbfac6b" width="250">
- select ros_driver.urp
- now you should give your computers ip to the robot. go to installation - external control. Change the host ıp part. You can use the ```ifconfig``` command to see your ip. 
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/e6082ef2-543f-43d7-bfb8-5c9efa1e0c4c" width="250">
- now go to 'program' section, you will see the play button at the bottom. Click that. Now you should see the screen below:
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/03fe8d37-4b37-4db2-af0c-603ea2fbbe0f" width="250">
- click the button that says start two times. Then click OK. Now you should be back at the program section.
- Before running any other scripts, you may want to lower the robot from its initial position. To do this, first make sure that the robot is not running. At the button of the program section, make sure the play button is not pressed.
- Now, there is a black button at the back-top of the controller. While holding that button, you should be able to move the robot manually to any position that you want. Do not apply too much force on the robot! It should be very easy to move it manually. If it is not moving easily, follow the steps above again. 
- Move the robot manually so it points downward like the following. Make sure you are not in the reach of the robot's arm. 
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/8e49b7f4-400e-4e89-8c31-acf995e26550" width="250">
- Now return back to your computer. Open a terminal and run ```roscore```.
- Open another terminal to run the docker container. Run the following command: ```docker run --network host YOUR_TAG --robot_ip= ... gripper_ip= ... ``` You can check the robots ip and gripper ip by clicking the "UR" symbol on top left.
- You can run the scripts in your repo file. You might find the "demonstration.py" file useful. It collects the joint positions of the robot when it is running. So you can use it to collect the joint positions of the robot and execute them later to make the robot follow a trajectory. For instance, you can run this file when you are lowering the robot from its inital position. Then  you can run the saved trajectory to lower the robot automatically. IMPORTANT NOTE: if you want to use this code, make sure that robot is in the right position! For example if you want to lower the robot from its initial position, make sure the robot is in fact in the initial position!! if you run the trajectory that lower the robot when it is already lowered for example, the robot will probably hit the table or move unexpectedly!!
- You can write a safety check to prevent such accidents. Here in line 67 for example, there is a simple code that makes sure that the robot is indeed in the initial position before trying to move the robot: https://github.com/mertcan-ozkan/cmpe492/blob/main/cmpe492/real_ur10/environment_new.py
- Now, pressing the start button at the button of the "program" section will move the robot. As mentioned above you can make the robot follow a saved trajectory using the demonstration.py. Before you run your python file, makes sure that you clicked the start button so the robot is already running. If you first run your python code and then press the start button, the robot might move unexpectedly fast!
- There is also a stop button at the bottom of the program section to stop the robot. Make sure that you are not using the robot at full speed! At the program section, there is also a slider that controls the speed. You can lower that when you are running your script. Always use the robot at low speeds if you are new to UR10.
- You can also try to use the gamepad_controller file to move the robot using a gamepad. Make sure none of the buttons are being pressed, some of the buttons might be jammed! You can check this file to understand how you can control the robot using cartesian coordinates. 
- Lastly, there is a big red button on the controller, you can press it any time to stop the robot instantly.
- When you are done with the robot, first press the stop button. Then click the "move" section.
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/16261e2f-72d0-4a5a-af6b-3c62b62c55f0" width="250">
- This page helps you to move the robot. We will use it to move to robot to its initial position. Click home.
- <img src="https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/143467fa-6a0f-48d6-a434-c56c7ff92feb" width="250">
- Here click "auto" to move the robot to its initial position. Always move the robot to its initial position before closing the controller.
- After that, click file  and close the program to go to the first screen. Then you can close the controller using the button on the controller.

### Problems that you might encounter
- When you are using the robot, connection might get cut off. You might see an error mesage like below (or something similar):
- ![](https://github.com/mertcan-ozkan/ur10_setup/assets/74208991/806f8a83-3ef7-4b9c-9fba-73304387f4c5)
- In this case you might try to shut down ros and rerun the docker container. Also make sure that the ethernet cable is connected properly to your computer. If this does not solve the issue, close the controller and open it again. Then try to connect to the robot again by following the steps above.
