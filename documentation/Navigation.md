# [Navigation](http://wiki.ros.org/navigation)

## Overview

* inputs:  
  - odometry  
  - sensor data

* output:  
  - velosity command  

* pre-requisite:  
  - robot running ROS  
  - tf transform tree  
  - publish sensor data with correct  Message types  
  - navigation configuration

## Hardware Requirements  
  - differential and holonomic robots only  
  - planar laser data  
  - developed on square robot

## [Navigation Stack Setup](http://wiki.ros.org/navigation/Tutorials/RobotSetup)  

### Robot Setup  
1. ROS  
2. [Transform Configuration](http://wiki.ros.org/navigation/Tutorials/RobotSetup/TF)  
3. [Sensor Information](http://wiki.ros.org/navigation/Tutorials/RobotSetup/Sensors)  
4. [Odometry Information](http://wiki.ros.org/navigation/Tutorials/RobotSetup/Odom)
5. Base Controller  
6. Mapping