find_package(PbOSCommon REQUIRED)

add_executable(bootldx
    "init.S"
    "main.c"
    "error.h" "error.c"
    "kloader.h" "kloader.c"
    "mb.h" "mb.c"
    "misc.h"
    "../display/vga.c")

target_include_directories(bootldx SYSTEM BEFORE PRIVATE ${FreeSTDC_INCLUDE_DIR})
target_include_directories(bootldx PUBLIC ${PbOSCommon_INCLUDE_DIR})
add_dependencies(bootldx pbarch freestdc)
target_link_libraries(bootldx pbarch freestdc)
target_link_options(bootldx PRIVATE "-T${CMAKE_CURRENT_SOURCE_DIR}/bootldr.lds")

add_custom_target(bootldr
    COMMAND ${CMAKE_OBJCOPY} --strip-debug -O binary $<TARGET_FILE:bootldx> ${PROJECT_BINARY_DIR}/bootldr
    BYPRODUCTS ${PBOS_BINARY_DIR}/bootldr
    DEPENDS bootldx)
