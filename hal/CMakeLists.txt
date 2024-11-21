find_package(PbOSCommon REQUIRED)

file(GLOB SRC *.c *.h)
add_library(hal ${SRC})
target_include_directories(hal PUBLIC ${PbOSCommon_INCLUDE_DIR})
add_subdirectory(${CMAKE_SYSTEM_PROCESSOR})
