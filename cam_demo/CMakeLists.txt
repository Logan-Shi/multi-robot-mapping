cmake_minimum_required(VERSION 2.8.3)
project(cam_demo)

find_package(catkin REQUIRED
sensor_msgs
cv_bridge
roscpp
std_msgs
image_transport
)

generate_messages(
  DEPENDENCIES
  std_msgs
)

include_directories(
  include_directories(include ${catkin_INCLUDE_DIRS})
)

add_executable(image_converter src/image_converter.cpp)
target_link_libraries(image_converter ${catkin_LIBRARIES})
add_dependencies(image_converter cam_demo_image_converter_cpp)

   find_package(OpenCV)
   include_directories(${OpenCV_INCLUDE_DIRS})
   target_link_libraries(image_converter ${OpenCV_LIBRARIES})
