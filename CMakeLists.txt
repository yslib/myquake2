cmake_minimum_required(VERSION 3.12)

project(myquake2)

set(CMAKE_POSITION_INDEPENDENT_CODE ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Operating system.
set(YQ2OSTYPE "${CMAKE_SYSTEM_NAME}" CACHE STRING "Override operation system type")
add_definitions(-DYQ2OSTYPE="${YQ2OSTYPE}")

# Architecture string.
set(YQ2ARCH "${CMAKE_SYSTEM_PROCESSOR}" CACHE STRING "Override CPU architecture")
string(REGEX REPLACE "amd64" "x86_64" ARCH "${YQ2ARCH}")
string(REGEX REPLACE "i.86" "i386" ARCH "${ARCH}")
string(REGEX REPLACE "^arm.*" "arm" ARCH "${ARCH}")
add_definitions(-DYQ2ARCH="${ARCH}")
add_subdirectory(src)
