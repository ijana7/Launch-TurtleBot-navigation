# Launch-TurtleBot-navigation

This repository contains the ROS (Robot Operating System) packages and configuration files for the Turtlebot3 robot platform.

## Introduction
Turtlebot3 is an open-source, low-cost, and programmable robot platform designed for education, research, and development. This repository provides a complete ROS workspace for working with the Turtlebot3 in simulation and on the physical robot.

## Prerequisites
- ROS Noetic (Ubuntu 20.04)
- Gazebo simulation environment
- Turtlebot3 hardware (Burger, Waffle, or Waffle Pi)

## Installation
1. Create a new ROS workspace:


## Learn about TrutleBot3

ROBOTIS e-Manual

Turtulebot3 package

Turtulebot3_simulation package

## Setup Your Envioremnt

1. Install Ubuntu 20.04:
   - Step By Step [How to Install Ubuntu 20.04](https://github.com/alanoudmk/Install-Ubuntu-20.04.6-On-VirtualBox).
     
2. Open a **Terminal**: 
   > Ctrl + Alt + T

  
3. Install ROS Noetic on Remote PC: 
  - Step By Step [How to Install ROS Noetic 20.04.6](https://github.com/alanoudmk/Install-ROS-Noetic-on-Ubuntu)
  - Or:
```
  $ sudo apt update
  $ sudo apt upgrade
  $ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
  $ chmod 755 ./install_ros_noetic.sh 
  $ bash ./install_ros_noetic.sh
```
4. Install Dependent ROS Packages:
```
  $ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
```
5. Install TurtleBot3 Packages:
```
   $ sudo apt install ros-noetic-dynamixel-sdk
   $ sudo apt install ros-noetic-turtlebot3-msgs
   $ sudo apt install ros-noetic-turtlebot3
```

***



# Gazebo Simulation
The [Gazebo Simulation](https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#gazebo-simulation) is a powerful tool for TurtleBot3 development and testing, as it allows you to experiment with different algorithms, sensors, and behaviors without the risk of damaging the physical robot or the environment. 

## 1. Create Workspace:
   
1. Open a **Terminal** & Source the ROS 1 Noetic: 
   > Ctrl + Alt + T
```
  $ source /opt/ros/noetic/setup.bash
  $ echo $ROS_DISTRO
```
 - The output should be "noetic".

   
2. Create the Workspace Directory & Source Folder:
```
  $ cd
  $ mkdir -p ~/my_turtlebot_ws/src
```

2. Create The & Build the Workspace:  

  ```
    $ catkin_make
    $ source devel/setup.bash
  ```

4. Source Catkin Workspace: 

 ```
   $ cd devel/
   $ source setup.bash 
  ```

***

###  Empty World:
```
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

<img width="1101" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٥ ١٧ ص" src="https://github.com/user-attachments/assets/179d5722-665b-41bb-9468-cfdb1c3c8d4d">
<img width="1184" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٥ ٤٧ ص" src="https://github.com/user-attachments/assets/dc7f3a7f-ee78-468e-a6d3-fa4527b180a3">

### TurtleBot3 World:
```
  $ export TURTLEBOT3_MODEL=waffle
  $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
<img width="1177" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٦ ٥٢ ص" src="https://github.com/user-attachments/assets/83cc4402-0189-4cbf-855a-ac8504f88a49">

###  TurtleBot3 House:
```
  $ export TURTLEBOT3_MODEL=waffle_pi
  $ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
<img width="1173" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٨ ١٩ ص" src="https://github.com/user-attachments/assets/f23b5a6e-c48d-419e-b473-15e17832b5d0">

## 4. Operate TurtleBot3 
Launch the teleoperation node with below command in a new terminal window.
```
  $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```



Uploading 1721889392074382.mp4…

