cmake_minimum_required(VERSION 3.20.1)

project(test1 CXX)

add_library(test1
  inc/test1.h
  src/test1.cpp
)
add_library(test1::test1 ALIAS test1)

target_include_directories(test1
  PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/inc>
    $<INSTALL_INTERFACE:inc>
)

install(TARGETS
  test1
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)
#install(DIRECTORY inc/test1 DESTINATION include)
