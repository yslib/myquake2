set(MODULE_NAME "client")

set(MODULE_SHARED_OR_STATIC "STATIC")

set(MODULE_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")

find_package(SDL2 REQUIRED)

set(MODULE_SRC)
aux_source_directory(. MODULE_SRC)

set(CURL_SUB_SRC)
aux_source_directory(./curl CURL_SUB_SRC)

set(INPUT_SUB_SRC)
aux_source_directory(./input INPUT_SUB_SRC)

set(MENU_SUB_SRC)
aux_source_directory(./menu MENU_SUB_SRC)

set(SOUND_SUB_SRC)
aux_source_directory(./sound SOUND_SUB_SRC)

set(VID_SUB_SRC)
aux_source_directory(./vid VID_SUB_SRC)

list(APPEND MODULE_SRC ${CURL_SUB_SRC} ${INPUT_SUB_SRC} ${MENU_SUB_SRC} ${SOUND_SUB_SRC} ${VID_SUB_SRC})

add_subdirectory(refresh)

add_library(${MODULE_NAME} ${MODULE_SHARED_OR_STATIC})
target_sources(${MODULE_NAME} PRIVATE ${MODULE_SRC})
target_link_libraries(${MODULE_NAME} PRIVATE common server SDL2::SDL2main SDL2::SDL2 game unix)
target_include_directories(${MODULE_NAME} PUBLIC ${MODULE_INCLUDE_DIR})
