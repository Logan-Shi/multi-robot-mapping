# camera  
```sh
roscore
rosrun usb_cam usb_cam_node
rosrun image_view image_view image:=/usb_cam/image_raw
roslaunch usb_cam usb_cam-test.launch (video0->video1)
rosrun cam_demo image_converter
```