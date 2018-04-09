# Policy
cmake_minimum_required( VERSION 3.0) 


# Project name
project(openTRJ CXX C)

include(${CMAKE_SOURCE_DIR}/cmake/macros.cmake)

if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()
if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
    set(CMAKE_CXX_FLAGS "-std=c++11 -O3")        ## Optimize	
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
   set(CMAKE_CXX_FLAGS "-std=c++11 -O3 -ffast-math -fno-math-errno")  
endif()
if ("${CMAKE_C_COMPILER_ID}" STREQUAL "Clang")
    set(CMAKE_C_FLAGS " -O2 ")        ## Optimize	
elseif ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
   set(CMAKE_C_FLAGS "-O2 -fmessage-length=0") 
endif()

if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set (CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}" CACHE PATH "default install path" FORCE )
endif()
LONG_TODAY(BUILD_DATE)

add_subdirectory(alglib)
add_subdirectory(voro++)
add_subdirectory(xdr)
add_executable(trjVoronoi trjVoronoi.cpp)
add_executable(trjProp trjProp.cpp)
target_link_libraries(trjVoronoi xdrfile voro++ alglib)
target_link_libraries(trjProp xdrfile voro++ alglib)
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
