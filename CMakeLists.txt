cmake_minimum_required (VERSION 2.6)
project (cpp-cmake)
add_executable(cpp-cmake helloworld.cpp)

set_property(TARGET cpp-cmake PROPERTY CXX_STANDARD 11)
set_property(TARGET cpp-cmake PROPERTY CXX_STANDARD_REQUIRED ON)

find_package(Doxygen)
if (DOXYGEN_FOUND)
  add_custom_command(OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/html/index.html
    COMMAND ${DOXYGEN_EXECUTABLE} ${CMAKE_CURRENT_BINARY_DIR}/DOXYFILE
    DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/DOXYFILE
    COMMENT "Build doxygen documentation")
  add_custom_target(html DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/html/index.html)
endif()
