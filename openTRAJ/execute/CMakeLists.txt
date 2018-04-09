# Policy
cmake_minimum_required( VERSION 3.0) 


if (NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Release")
endif()
set(SOURCE ExecuteVoronoi.cpp TrjRead.cpp  trjInput.cpp ClearUsage.cpp ExecuteProp.cpp trjInput.cpp ClearUsage.cpp)
	
add_library(Execute STATIC ${SOURCE})
include_directories("./" "${PROJECT_SOURCE_DIR}/libtraj" "${PROJECT_SOURCE_DIR}/Molecules" "${PROJECT_SOURCE_DIR}/Voronoi" )

