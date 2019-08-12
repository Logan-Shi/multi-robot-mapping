# rplidar 

```
ls -l /dev |grep ttyUSB                      (check if connected)
sudo chmod 666 /dev/ttyUSB0                  (authorize)
roslaunch rplidar_ros rplidar_a3.launch (for A3)
roslaunch rplidar_ros rplidar.launch    (for A1 or A2)
```

# kinect2 

```
roslaunch kinect2_bridge kinect2_bridge.launch
(optional)rosrun kinect2_viewer kinect2_viewer (sd hd qhd)
```

# camera  

```
rosrun usb_cam usb_cam_node
rosrun image_view image_view image:=/usb_cam/image_raw
roslaunch usb_cam usb_cam-test.launch (video0->video1)
rosrun cam_demo image_converter
```