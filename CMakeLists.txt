cmake_minimum_required (VERSION 2.6)
project (ZBARCV)

set(CMAKE_MODULE_PATH ${ZBARCV_SOURCE_DIR})
find_package (OpenCV)
find_package (ZBar0)
find_package(CUDA)

file( GLOB  hdr *.hpp *.h )
file( GLOB  cu  *.cu)
SET (to_bw_files MOGTracking.cpp)

CUDA_ADD_EXECUTABLE(to_bw ${to_bw_files} ${hdr} ${cu})
target_link_libraries (to_bw ${OpenCV_LIBRARIES} ${ZBAR_LIBRARIES})
