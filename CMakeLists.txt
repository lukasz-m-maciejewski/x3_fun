cmake_minimum_required (VERSION 3.11.0)

execute_process(COMMAND /usr/bin/conan install ${CMAKE_SOURCE_DIR}
  WORKING_DIRECTORY ${CMAKE_BINARY_DIR})

project(drakmoor)
set(CONAN_SYSTEM_INCLUDES "On")
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

enable_testing()

project(x3_fun)

add_library(x3_fun
  src/expression.cpp
  src/interpreter.cpp
  src/printer.cpp)

target_include_directories(x3_fun PUBLIC
  ${CMAKE_SOURCE_DIR}/fun)

add_executable(eval_expression_test
  test/eval_expression_test.cpp)

target_link_libraries(eval_expression_test PUBLIC
  x3_fun
  boost_regex
  boost_filesystem
  boost_regex
  boost_system
  boost_regex
  boost_regex
  -lboost_regex)
