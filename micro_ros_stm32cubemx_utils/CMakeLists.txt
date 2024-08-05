add_library(micro_ros INTERFACE)

target_sources(micro_ros INTERFACE
    ${CMAKE_CURRENT_LIST_DIR}/extra_sources/custom_memory_manager.c
    ${CMAKE_CURRENT_LIST_DIR}/extra_sources/microros_allocators.c
    ${CMAKE_CURRENT_LIST_DIR}/extra_sources/microros_time.c
    ${CMAKE_CURRENT_LIST_DIR}/extra_sources/microros_transports/dma_transport.c
)

target_include_directories(micro_ros INTERFACE
    ${CMAKE_CURRENT_LIST_DIR}/microros_static_library/libmicroros/microros_include
)

target_link_directories(micro_ros INTERFACE
    ${CMAKE_CURRENT_LIST_DIR}/microros_static_library/libmicroros
)


find_library(MICROROS_LIB microros HINTS ${CMAKE_CURRENT_LIST_DIR}/microros_static_library/libmicroros)

target_link_libraries(micro_ros INTERFACE
#     # stm32cubemx
#     micro_ros_stm32cubemx_utils/microros_static_library/libmicroros/libmicroros.a
    ${MICROROS_LIB}
)