# Policy
cmake_minimum_required( VERSION 3.0) 


# Project name
project(xdr C)
if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()

if(CMAKE_COMPILER_IS_GNUCC)
    set(CMAKE_C_FLAGS "-O2")        ## Optimize
    set(CMAKE_EXE_LINKER_FLAGS "-s")  ## Strip binary
endif()

include(ConfigureChecks.cmake)
add_definitions(-DHAVE_CONFIG_H=1)
if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set (CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}" CACHE PATH "default install path" FORCE )
endif()

include_directories("${PROJECT_BINARY_DIR}")
message(STATUS "Here ${PROJECT_SOURCE_DIR}")
add_subdirectory(src)
