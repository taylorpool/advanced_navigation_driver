cmake_minimum_required(VERSION 3.16)
project(advanced_navigation_driver)

add_library(rs232
  src/rs232/rs232.c
)

add_library(advanced_navigation
  src/an_packet_protocol.c
  src/spatial_packets.c
)
target_link_libraries(advanced_navigation
  rs232
)

# add_executable(advanced_navigation_driver src/an_driver.cpp)
# target_link_libraries(advanced_navigation_driver
#   advanced_navigation
# )
