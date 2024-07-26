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

##  Empty World:
```
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```

<img width="1101" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٥ ١٧ ص" src="https://github.com/user-attachments/assets/179d5722-665b-41bb-9468-cfdb1c3c8d4d">
<img width="1184" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٥ ٤٧ ص" src="https://github.com/user-attachments/assets/dc7f3a7f-ee78-468e-a6d3-fa4527b180a3">

## TurtleBot3 World:
```
  $ export TURTLEBOT3_MODEL=waffle
  $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
<img width="1177" alt="‏لقطة الشاشة ١٤٤٦-٠١-١٩ في ٨ ٥٦ ٥٢ ص" src="https://github.com/user-attachments/assets/83cc4402-0189-4cbf-855a-ac8504f88a49">

##  TurtleBot3 House:
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


https://github.com/user-attachments/assets/b614a68b-3293-4fbc-a171-379033f3025c

## 1. Launch Simulation World
- Three Gazebo environments are prepared, but for creating a map with SLAM, it is recommended to use either ``TurtleBot3 World`` or ``TurtleBot3 House``.
- Please use the proper keyword among ``burger``, ``waffle``, ``waffle_pi`` for the TURTLEBOT3_MODEL parameter.

```
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

## 2. Run SLAM Node

1. Open a **Terminal** & Source the ROS 1 Noetic: 
```
  $ source /opt/ros/noetic/setup.bash
```

2. Run SLAM Node:
  - Gmapping SLAM method is used by default.
```
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
### 3. Run Teleoperation Node

1. Open a new **Terminal** & Source the ROS 1 Noetic: 

```
  $ source /opt/ros/noetic/setup.bash
```

2. Run Teleoperation Node:

```
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
### 4. Save The Map
When the map is created successfully:

1. Open a **Terminal** & Source the ROS 1 Noetic: 
```
  $ source /opt/ros/noetic/setup.bash
```

2. Save the map:
```
  $ rosrun map_server map_saver -f ~/map
```

> The saved map.pgm file


***

# Navigation Simulation
Just like the SLAM in Gazebo simulator, you can select or create various environments and robot models in [virtual Navigation world](https://emanual.robotis.com/docs/en/platform/turtlebot3/nav_simulation/).

Proper map has to be prepared before running the Navigation. Other than preparing simulation environment instead of bringing up the robot, Navigation Simulation is pretty similar to that of Navigation.

# 1. Launch Simulation World

1. Terminate all applications:

2. Launch Simulation World
 - In the previous SLAM section, TurtleBot3 World is used to creat a map. The same Gazebo environment will be used for Navigation.
 - Please use the proper keyword among ``burger``, ``waffle``, ``waffle_pi`` for the TURTLEBOT3_MODEL parameter.
 
```
  $ source /opt/ros/noetic/setup.bash
  $ source ~/my_turtlebot_ws/devel/setup.bash
  $ cd  my_turtlebot_ws/
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```


# 2. Run Navigation Node

1. Open a **Terminal** & Source the ROS 1 Noetic: 
```
  $ source /opt/ros/noetic/setup.bash
  $ source ~/my_turtlebot_ws/devel/setup.bash 
```

2. Run Navigation Node:
```
  $ export TURTLEBOT3_MODEL=burger
  $ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
```


# 3. Estimate Initial Pose

- Initial Pose Estimation
  - must be performed before running the Navigation as this process initializes the AMCL parameters that are critical in Navigation.
  - TurtleBot3 has to be correctly located on the map with the LDS sensor data that neatly overlaps the displayed map.


4. Click the ``2D Pose Estimate`` button in the RViz menu.

 5. Set Navigation Goal

1. Click the ``2D Nav Goal`` button in the RViz menu.
