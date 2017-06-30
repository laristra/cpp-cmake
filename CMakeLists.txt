cmake_minimum_required (VERSION 2.6)
project (cpp-cmake)
add_executable(cpp-cmake helloworld.cpp)

set_property(TARGET cpp-cmake PROPERTY CXX_STANDARD 11)
set_property(TARGET cpp-cmake PROPERTY CXX_STANDARD_REQUIRED ON)
