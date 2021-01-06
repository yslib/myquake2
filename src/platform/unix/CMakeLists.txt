set(MODULE_NAME "unix")

set(MODULE_SHARED_OR_STATIC "STATIC")

set(MODULE_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")

set(MODULE_SRC)
aux_source_directory(. MODULE_SRC)

set(SHARED_SUB_SRC)
aux_source_directory(./shared SHARED_SUB_SRC)

set(GENERIC_SRC "../generic/misc.c")


list(APPEND MODULE_SRC ${SHARED_SUB_SRC} ${GENERIC_SRC})

add_subdirectory(real_main)

add_library(${MODULE_NAME} ${MODULE_SHARED_OR_STATIC})
target_sources(${MODULE_NAME} PRIVATE ${MODULE_SRC})
target_link_libraries(${MODULE_NAME} PRIVATE common client server ${yquake2LinkerFlags} game)
target_include_directories(${MODULE_NAME} PUBLIC ${MODULE_INCLUDE_DIR})
