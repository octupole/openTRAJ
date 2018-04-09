# Policy
cmake_minimum_required( VERSION 3.0) 


# Project name
project(openTRJ CXX C)

include(${CMAKE_SOURCE_DIR}/cmake/macros.cmake)

if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()

if(CMAKE_COMPILER_IS_GNUCC)
    set(CMAKE_C_FLAGS "-O2")        ## Optimize
    set(CMAKE_EXE_LINKER_FLAGS "-s")  ## Strip binary
endif()

LONG_TODAY(BUILD_DATE)

add_subdirectory(xdr)
add_executable(main main.cpp)
target_link_libraries(main xdrfile)
include_directories("${PROJECT_SOURCE_DIR}/xdr/include")
message( STATUS)
message( STATUS "========== XDR Build Information ==========")
message( STATUS "Current date/time .......... = ${BUILD_DATE}")
message( STATUS "CMAKE_SYSTEM ............... = ${CMAKE_SYSTEM}")
message( STATUS "==============================================")
message( STATUS "CMAKE_BUILD_TYPE ........... = ${CMAKE_BUILD_TYPE}")
message( STATUS "CMAKE_INSTALL_PREFIX ....... = ${CMAKE_INSTALL_PREFIX}")
message( STATUS "CMAKE_C_COMPILER ........... = ${CMAKE_C_COMPILER}")
message( STATUS "CMAKE_CXX_COMPILER ......... = ${CMAKE_CXX_COMPILER}")
