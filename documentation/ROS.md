# INSTALL

---

## ros install

```sh
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116

sudo apt-get update

sudo apt-get install ros-kinetic-desktop-full
```

## ros setup

```sh
sudo rosdep init
rosdep update

echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc

sudo apt install python-rosinstall python-rosinstall-generator python-wstool build-essential

printenv | grep ROS

source /opt/ros/kinetic/setup.bash

mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make

source devel/setup.bash

echo $ROS_PACKAGE_PATH
```

if setup correctly, the output should be ```/home/youruser/catkin_ws/src:/opt/ros/kinetic/share```

## create package

```
catkin_create_pkg [pkg_name] depend1 depend2
```

## roslaunch can't find package

error output:

```sh
ResourceNotFound: rrt_exploration_tutorials
ROS path [0]=/opt/ros/kinetic/share/ros
ROS path [1]=/opt/ros/kinetic/share
```
  - try ```source devel/setup.bash```
  - check ```sudo gedit ~/.bashrc```

---

# COMMANDS

---

* roscd  

* rostopic  
	- list  
	- echo  
	- pub  

* rosrun  
	- remap:  
		```
		rosrun robot_sim_demo robot_keyboard_teleop.py /cmd_vel_mux/input/teleop:=/robot_1/cmd_vel
		```  

* roslaunch  

---

# Debug Tools

---

* roswtf  

* rosrun rqt_graph rqt_graph  

* rosrun rqt_tf_tree rqt_tf_tree  