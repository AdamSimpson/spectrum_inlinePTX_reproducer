cmake_minimum_required(VERSION 3.1)
project(inline_ptx_nvrtc)

find_package(CUDA REQUIRED)

file(GLOB SRC_FILES ${CMAKE_SOURCE_DIR}/*.cu ${CMAKE_SOURCE_DIR}/*.cpp)

include_directories(${CMAKE_SOURCE_DIR}/inc)

link_directories(${CUDA_TOOLKIT_ROOT_DIR}/lib64)
link_libraries(nvrtc cuda ${CUDA_LIBRARIES})

cuda_add_executable(inlinePTX_nvrtc ${SRC_FILES})
