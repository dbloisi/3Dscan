cmake_minimum_required(VERSION 2.8.3)
project(scan_3d)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  roscpp
  sensor_msgs
  std_msgs
)

find_package(OpenCV 4.2 REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

catkin_package()

include_directories(
  src/
  ${catkin_INCLUDE_DIRS}
)

set(SRCS src/scan_3d.cpp)

add_executable(scan_3d ${SRCS})

target_link_libraries(3Dscan
  ${catkin_LIBRARIES}
  ${OpenCV_LIBRARIES}
)

