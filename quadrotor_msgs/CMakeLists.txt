cmake_minimum_required(VERSION 2.8.12)
project(quadrotor_msgs)

add_compile_options(-std=c++11)

# set default build type
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE RelWithDebInfo)
endif()

find_package(catkin REQUIRED COMPONENTS message_generation geometry_msgs std_msgs rosconsole)
find_package(Eigen3 REQUIRED)

include_directories(${catkin_INCLUDE_DIRS} ${EIGEN3_INCLUDE_DIR})

add_message_files(DIRECTORY msg
  FILES
  AuxCommand.msg
  Corrections.msg
  OutputData.msg
  PositionCommand.msg
  PWMCommand.msg
  MotorSpeed.msg
  Serial.msg
  SO3Command.msg
  StatusData.msg
  TRPYCommand.msg
  FlatOutputs.msg
  )

generate_messages(
  DEPENDENCIES geometry_msgs std_msgs)

catkin_package(
  INCLUDE_DIRS
  LIBRARIES
  CATKIN_DEPENDS message_runtime geometry_msgs std_msgs
  DEPENDS EIGEN3)

