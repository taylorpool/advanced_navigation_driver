cmake_minimum_required(VERSION 3.16)
project(advanced_navigation_driver)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
)

catkin_package(
  CATKIN_DEPENDS roscpp std_msgs
)

add_library(rs232
  src/rs232/rs232.c
)

add_library(advanced_navigation
  src/an_packet_protocol.c
  src/spatial_packets.c
)

add_executable(advanced_navigation_driver
  src/an_driver.cpp
)
target_link_libraries(advanced_navigation_driver
  ${catkin_LIBRARIES}
  advanced_navigation
  rs232
)
target_include_directories(advanced_navigation_driver
  PUBLIC
  ${catkin_INCLUDE_DIRS}
)
