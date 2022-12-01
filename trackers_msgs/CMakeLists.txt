cmake_minimum_required(VERSION 2.8.3)
project(trackers_msgs)

# set default build type
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE RelWithDebInfo)
endif()

find_package(catkin REQUIRED COMPONENTS message_generation actionlib_msgs std_msgs geometry_msgs)

include_directories(${catkin_INCLUDE_DIRS})

add_service_files(DIRECTORY srv
  FILES
  Transition.srv
)

add_action_files(DIRECTORY action
  FILES
  LineTracker.action
  VelocityTracker.action
  QuadrotorPathTracker.action
  CircleTracker.action
  TrajectoryTracker.action
  LissajousTracker.action
  LissajousAdder.action)


add_message_files(DIRECTORY msg
  FILES
  TrackerStatus.msg
)

generate_messages(DEPENDENCIES actionlib_msgs std_msgs geometry_msgs)

catkin_package(
  INCLUDE_DIRS 
  LIBRARIES 
  CATKIN_DEPENDS message_runtime geometry_msgs actionlib_msgs std_msgs 
  DEPENDS
)

