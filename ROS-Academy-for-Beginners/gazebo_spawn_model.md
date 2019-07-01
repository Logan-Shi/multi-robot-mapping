# Gazebo_spawn_model  
## URDF(unified Robot Discription File)  
+ link: origin, geometry, collision  
```xml  
  <link name="link1">
    <visual>
      <origin rpy="0 -1.57 0" xyz="0 0 0"/>
      <geometry>
        <mesh filename="package://urdf_csdn/urdf/mesh/knife.stl"/>
      </geometry>
    </visual>

    <collision>
      <origin xyz="0.0 0 0.0" rpy="0 0 0" />
      <geometry>
        <cylinder length="0.6" radius="0.2" />
      </geometry>
    </collision>

  </link>  
```  

+ joint: links, origin, axis, limit  
```xml
  <joint name="joint1" type="continuous">
    <parent link="link1"/>
    <child link="link2"/>
    <origin xyz=".5 .3 0.7" rpy="0 0 0"/>
    <axis xyz="0 1 0"/>
    <limit lower="-3.14" upper="3.14" effort="150.0" velocity="3.15"/>
  </joint>
```  

## XACRO