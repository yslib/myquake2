
set(MODULE_NAME "common")

set(MODULE_SHARED_OR_STATIC "STATIC")

set(MODULE_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")

set(MODULE_SRC)
aux_source_directory(. MODULE_SRC)

set(SHARED_SRC)
aux_source_directory(./shared SHARED_SRC)


set(UNZIP_SRC)
aux_source_directory(./unzip UNZIP_SRC)

list(APPEND MODULE_SRC ${SHARED_SRC} ${UNZIP_SRC})


add_library(${MODULE_NAME} ${MODULE_SHARED_OR_STATIC})
target_sources(${MODULE_NAME} PRIVATE ${MODULE_SRC})
target_link_libraries(${MODULE_NAME} PRIVATE client server unix)
target_include_directories(${MODULE_NAME} PUBLIC ${MODULE_INCLUDE_DIR})
