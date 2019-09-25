# multi-robot-mapping

---

## Simulation

### single bot mapping with irobotcreate

```
$ roslaunch rrt_exploration_tutorials single_simulated_irobotcreate.launch
$ roslaunch rrt_exploration single.launch
```

### logics

1. meshes

2. world

3. `irobotcreate.launch.xml`  
	* gazebo_spawn_model  
	* robot_state_publisher(tf)

4. `move_baseSafe.launch`  
	* `rosrun slam_gmapping`  
	* `rosrun move_base_node`

5. target generation  
  `rrt_exploration/single.launch`  
	* global detector  
	* local detector  
	* filter  
	* assigner

---

## Experiment

### single bot mapping experiment

```
$ roslaunch rrt_exploration_tutorials single_experiment_irobotcreate.launch
$ roslaunch rrt_exploration single.launch
```

### Hardware Requirements

1. Sensor Information 

2. Odom and tf

3. Base controller