# Policy
cmake_minimum_required( VERSION 2.8) 

# Project name
#project(xdr-cmake C)

# be more CDT Error Parser friendly..
IF(CMAKE_COMPILER_IS_GNUCC)
  SET(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fmessage-length=0 ")
ENDIF(CMAKE_COMPILER_IS_GNUCC)

include_directories("${PROJECT_SOURCE_DIR}/include")
add_library(xdrfile STATIC xdrfile_seek.c xdrfile_trr.c xdrfile_xtc.c xdrfile.c)
install(TARGETS xdrfile ARCHIVE DESTINATION "${CMAKE_INSTALL_PREFIX}/lib" COMPONENT library)
