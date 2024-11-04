cmake_minimum_required(VERSION 3.10)
project(gl VERSION 0.1.0)
cmake_policy(SET CMP0072 NEW)

set(CMAKE_CXX_STANDARD 20)

find_package(OpenGL REQUIRED)

add_executable(gl
 src/main.cpp 
 src/glad.c
)

target_link_libraries(gl glfw OpenGL::GL)

include_directories(${CMAKE_SOURCE_DIR}/include)

if(WIN32)
  message(STATUS "Configuring for Windows")
  set(GENERATOR "MinGW Makefiles")  # или "Visual Studio 16 2019"
elseif(APPLE)
  message(STATUS "Configuring for macOS")
  set(GENERATOR "Xcode")
elseif(UNIX)
  message(STATUS "Configuring for Unix/Linux")
  set(GENERATOR "Unix Makefiles")
endif()