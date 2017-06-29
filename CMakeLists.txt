cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
set(CMAKE_LEGACY_CYGWIN_WIN32 0)

project("cpp-cmake")

enable_testing()


add_executable(hello helloworld.cpp
                    hello.cpp)
