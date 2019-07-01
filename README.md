# multi-robot-mapping

---

## Simulation

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