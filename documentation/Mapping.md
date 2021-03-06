## draw the map

```sh
roslaunch turtlebot_gazebo turtlebot_world.launch
rosrun gmapping slam_gmapping
roslaunch turtlebot_teleop keyboard_teleop.launch
rosrun rviz rviz
rosrun map_server map_saver -f (mapname_no_suffix)
```

## navigation demo with turtlebot

```sh
roslaunch turtlebot_gazebo turtlebot_world.launch
roslaunch turtlebot_gazebo amcl_demo.launch map_file:=~/demo.yaml
roslaunch turtlebot_rviz_launchers view_navigation.launch
```

## keyboard control

```sh
rosrun turtlesim turtle_teleop_key /turtle1/cmd_vel:=/cmd_vel
rosrun robot_sim_demo robot_keyboard_teleop.py /cmd_vel_mux/input/teleop:=/robot_1/cmd_vel
```

## active slam simulation

```sh
roslaunch rrt_exploration_tutorial single_tab_house.launch
roslaunch rrt_exploration single.launch
```
publish point manully

## frontier exploration

```sh
roslaunch navigation_stage move_base_gmapping_5cm.launch
roslaunch frontier_exploration global_map.launch
```
add Marker topic to select certain area to explore

## Stage

* [Tutorial](http://wiki.ros.org/turtlebot_stage/Tutorials/indigo/Customizing%20the%20Stage%20Simulator)

* [User Guide](http://playerstage.sourceforge.net/doc/stage-cvs/group__stage.html)

## Cartographer

rosservice call /finish_trajectory 0
rosservice call /write_state "{filename: '${HOME}/Downloads/mymap.pbstream'}"
rosrun cartographer_ros cartographer_pbstream_to_ros_map -map_filestem=${HOME}/Downloads/mymap -pbstream_filename=${HOME}/Downloads/mymap.pbstream -resolution=0.05