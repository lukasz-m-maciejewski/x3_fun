cmake_minimum_required (VERSION 3.11.0)

execute_process(COMMAND /usr/bin/conan install ${CMAKE_SOURCE_DIR}
  WORKING_DIRECTORY ${CMAKE_BINARY_DIR})

project(drakmoor)
set(CONAN_SYSTEM_INCLUDES "On")
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

project(x3_fun)

add_library(x3_fun
  src/expression.cpp
  src/interpreter.cpp
  src/printer.cpp)
