cmake_minimum_required (VERSION 2.6)
project (cpp-cmake)
add_executable(cpp-cmake helloworld.cpp)

set_property(TARGET cpp-cmake PROPERTY CXX_STANDARD 11)
set_property(TARGET cpp-cmake PROPERTY CXX_STANDARD_REQUIRED ON)

option(ENABLE_COVERAGE_BUILD "Do a coverage build" ON)
if(ENABLE_COVERAGE_BUILD)
  message(STATUS "Enabling coverage build")
  set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} --coverage -O0")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --coverage -O0")
  set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} --coverage")
  set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} --coverage")
endif()

find_package(Doxygen)
if (DOXYGEN_FOUND)
  add_custom_command(OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/html/index.html
    COMMAND ${DOXYGEN_EXECUTABLE} ${CMAKE_CURRENT_BINARY_DIR}/DOXYFILE
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/DOXYFILE
    COMMENT "Build doxygen documentation")
  add_custom_target(html DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/html/index.html)
endif()

enable_testing()
add_test (TestRun cpp-cmake)
