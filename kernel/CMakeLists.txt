file(GLOB SRC *.c *.h *.S)
add_executable(pbkern ${SRC})

target_include_directories(pbkern SYSTEM BEFORE PRIVATE ${FreeSTDC_INCLUDE_DIR})
set_target_properties(pbkern PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR})

add_dependencies(pbkern
    bootldr
)
target_link_libraries(pbkern pbarch freestdc hal)
target_link_options(pbkern PRIVATE "-T${PROJECT_SOURCE_DIR}/scripts/ld/${CMAKE_SYSTEM_PROCESSOR}/kernel.lds")

add_subdirectory("exec")
add_subdirectory("io")
add_subdirectory("kf")
add_subdirectory("km")
add_subdirectory("fs")
