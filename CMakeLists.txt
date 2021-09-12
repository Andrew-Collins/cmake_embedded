cmake_minimum_required(VERSION 3.20.1)
include($ENV{CMAKE_TOOLCHAINS}/utils.cmake)
set(CMAKE_TOOLCHAIN_FILE $ENV{CMAKE_TOOLCHAINS}/arm-gcc-toolchain.cmake)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -specs=\"nosys.specs\"")
project(cmake_lib_test)

set(SOURCES src/main.cpp)

add_subdirectory(lib_test)

add_executable(${PROJECT_NAME}.elf ${SOURCES})

target_link_libraries(${PROJECT_NAME}.elf PRIVATE lib_test::lib_test)

# generate_object(${PROJECT_NAME}.elf .bin binary)

add_custom_target(${PROJECT_NAME}.bin ALL DEPENDS ${PROJECT_NAME}.elf)

