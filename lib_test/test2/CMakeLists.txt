cmake_minimum_required(VERSION 3.20.1)

project(test2 CXX)

add_library(test2
  inc/test2.h
  src/test2.cpp
)
add_library(test2::test2 ALIAS test2)

target_include_directories(test2
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/inc>
    $<INSTALL_INTERFACE:inc>
)

install(TARGETS
  test2
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)
#install(DIRECTORY inc/test2 DESTINATION include)
