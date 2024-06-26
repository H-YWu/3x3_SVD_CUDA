cmake_minimum_required(VERSION 3.27)
project(svd3x3 LANGUAGES CXX CUDA)

include(CheckLanguage)
check_language(CUDA)

find_package(CUDAToolkit REQUIRED)

add_executable(svd3x3 svd3x3/kernel.cu)

target_include_directories(svd3x3 PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/svd3x3
    ${CUDAToolkit_INCLUDE_DIRS}
)

target_link_libraries(svd3x3 PRIVATE
    CUDA::cudart
    cudadevrt
)