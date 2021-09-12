cmake_minimum_required(VERSION 3.20.1)

project(lib_test)

add_subdirectory(test1)
add_subdirectory(test2)

add_library(lib_test INTERFACE)
add_library(lib_test::lib_test ALIAS lib_test)

target_link_libraries(lib_test
    INTERFACE
    test1::test1
    test2::test2
)

