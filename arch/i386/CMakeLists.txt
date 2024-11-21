find_package(PbOSCommon REQUIRED)

file(GLOB_RECURSE SRC *.c *.h *.asm *.s *.S)
add_library(pbarch ${SRC})
target_include_directories(pbarch PUBLIC ${PbOSCommon_INCLUDE_DIR})
