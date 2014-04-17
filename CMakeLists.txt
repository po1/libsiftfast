cmake_minimum_required (VERSION 2.8.3)
project (libsiftfast)

find_package(catkin REQUIRED)
find_package(OpenMP)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES siftfast
)

include_directories(include)

# OpenMP
if(OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()

# SSE
include(UseSSE.cmake)

add_library(siftfast SHARED src/libsiftfast.cpp)

install(TARGETS siftfast DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION})
