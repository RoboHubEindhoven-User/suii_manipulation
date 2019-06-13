# suii_manipulation

UR3 manipulation package for mobile robot Suii. This package is used to do pick and place tasks with the UR3 robotic arm on top of Suii. This README is used to explain how to install the suii_manipulation and the other required packages, and what steps must be taken to get everything running. 

If you to know more about this package you can visit the suii_manipulation [wiki](https://github.com/RoboHubEindhoven/suii_manipulation/wiki).

## Getting started

For this project it is assumed you use Ubuntu 16.04 LTS with ROS Kinetic

### Prerequisites

What things you need to install the software and how to install them:

You will need the ur_modern_driver package from ThomasTimm. You can intall this package by running the following lines:

```
cd catkin_ws/src
git clone https://github.com/ThomasTimm/ur_modern_driver.git
catkin_make
sudo apt-get install ros-kinetic-ur-*
```

This will give you the ability to run your program on a real Universal robot (UR3, UR5, UR10).

**Beaware that you need to change the ur_modern_driver/src/ur_hardware_interface.cpp to the ur_hardware_interface.cpp that is uploaded to this github. Copy it and paste it in your catkin_ws/src/ur_modern_driver/src. Don't forget to delete the old one.**

The next thing you will need to install is the universal_robot package. You can install this package by running the following lines:

```
cd catkin_ws/src
git clone https://github.com/ros-industrial/universal_robot.git
catkin_make
```
**Beaware that you need to change the universal_robot/ur_driver/src/ur_driver/io_interface.py to the io_interface.py that is uploaded to this github. Copy it and paste it in your catkin_ws/src/universal_robot/ur_driver/src/ur_driver. Don't forget to delete the old one.**

**You will need to add the ur3_suii.launch launch file that is uploaded to this github, to the ur_modern_driver/launch folder.**

The final package you will need are the Suii packages. These packages are located in [this github repository](https://github.com/RoboHubEindhoven/suii.git). To install these packages run the following lines.

```
cd catkin_ws/src
git clone https://github.com/RoboHubEindhoven/suii.git
catkin_make
```

## Installing suii_manipulation package

To install the suii_manipulation package in your catkin workspace, you will need to run the following lines:

```
cd catkin_ws/src
git clone https://github.com/RoboHubEindhoven/suii_manipulation.git
catkin_make
```

## Test your installed package

To test if your package is installed correctly run:

**This needs to run on Suii, if want to test on another device look to the next chapter (Using UR simulator)**

```
roslaunch ur_modern_driver ur3_suii.launch
rosrun suii_manipulation Manipulaiton.py
```

If this runs without errors, the package is installed correctly.

## Using UR simulator

It is also possible to use the simulator of UR. The offline simulator is available [here](https://www.universal-robots.com/download/?option=16594#section16593). We used version 3.4.5-100, this worked for us. After downloading the offline simulator, unpack it in a folder you prefer.

### Test offline simulator

To test the offline simulator, run the following line from the folder where your offline simulator is located.

```
./ursim-3.4.5-100/start-ursim.sh UR3
roslaunch suii_description display.launch
roslaunch ur_modern_driver ur3_suii.launch robot_ip:=localhost
```
To check if the Suii and the UR3 models are loaded:

```
rosrun rviz rviz
```

And add **RobotModel** to rviz.


