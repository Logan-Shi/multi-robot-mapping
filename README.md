# multi-robot-mapping

---

## Simulation

1. meshes

2. world

3. `irobotcreate.launch.xml`  
  1. gazebo_spawn_model  
  2. robot_state_publisher(tf)

4. `move_baseSafe.launch`  
  1. `rosrun slam_gmapping`  
  2. `rosrun move_base_node`

5. target generation  
  `rrt_exploration/single.launch`  
  1. global detector  
  2. local detector  
  3. filter  
  4. assigner