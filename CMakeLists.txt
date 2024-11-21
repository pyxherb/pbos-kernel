cmake_minimum_required(VERSION 3.23)
project(PbOSKernel VERSION 0.1.0)

enable_language(ASM)

include_directories(${PROJECT_SOURCE_DIR})
include_directories(${PROJECT_SOURCE_DIR}/include)

find_package(FreeSTDC REQUIRED)

add_freestdc_build(freestdc ${CMAKE_CURRENT_BINARY_DIR}/freestdc)

add_subdirectory("arch")
add_subdirectory("hal")
add_subdirectory("kernel")
