cmake_minimum_required(VERSION 2.8.3)
project(wam_bringup)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  sensor_msgs
  std_msgs
  std_srvs
  tf
  wam_msgs
  wam_srvs
)

## System dependencies are found with CMake's conventions
find_package(Boost REQUIRED COMPONENTS system)
find_package(Barrett REQUIRED)

catkin_package(
   INCLUDE_DIRS include
#  LIBRARIES wam_node
#  CATKIN_DEPENDS geometry_msgs roscpp sensor_msgs std_msgs std_srvs tf wam_msgs wam_srvs
#  DEPENDS system_lib
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${BARRETT_INCLUDE_DIRS}
  include
)

add_executable(wam_bringup src/wam_bringup.cpp)
add_dependencies(wam_bringup wam_bringup_generate_messages_cpp)
target_link_libraries(wam_bringup ${catkin_LIBRARIES} ${BARRETT_LIBRARIES})
