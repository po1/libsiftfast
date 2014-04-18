cmake_minimum_required (VERSION 2.8.3)
project (libsiftfast)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

find_package(catkin REQUIRED)
find_package(OpenMP)

catkin_package(
  LIBRARIES siftfast
  CFG_EXTRAS libsiftfast-extras.cmake
)

# OpenMP
if(OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()

# SSE
include(cmake/UseSSE.cmake)

# Generate header with version number
set(PKG_DEVEL_INCLUDE ${CATKIN_DEVEL_PREFIX}/include/siftfast)
configure_file(siftfast.h.in ${PKG_DEVEL_INCLUDE}/siftfast.h)

include_directories(${CATKIN_DEVEL_PREFIX}/include)

add_library(siftfast SHARED src/libsiftfast.cpp)

# Install rules

install(TARGETS siftfast DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION})

install(FILES ${PKG_DEVEL_INCLUDE}/siftfast.h
  DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}/siftfast)
