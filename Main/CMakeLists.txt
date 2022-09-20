cmake_minimum_required(VERSION 3.23)
project(Main)

set(CMAKE_CXX_STANDARD 14)

add_executable(Main main.cpp)

add_library(Number STATIC IMPORTED)
set_target_properties(Number PROPERTIES INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/../Number)
set_target_properties(Number PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/../Number/cmake-build-debug/libNumber.a)
target_link_libraries(Main Number)

add_library(Vector SHARED IMPORTED)
set_target_properties(Vector PROPERTIES INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR}/../Vector)
set_target_properties(Vector PROPERTIES IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/../Vector/cmake-build-debug/libVector.so)
target_link_libraries(Main Vector)
