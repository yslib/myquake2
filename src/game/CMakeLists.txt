
set(MODULE_NAME "game")
set(MODULE_SHARED_OR_STATIC "STATIC")
set(MODULE_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")

set(MODULE_SRC)
aux_source_directory(. MODULE_SRC)

set(PLAYER_SUB_SRC)
aux_source_directory(./player PLAYER_SUB_SRC)

set(SAVE_GAME_SUB_SRC)
aux_source_directory(./savegame SAVE_GAME_SUB_SRC)

set(MONSTER_SUB_SRC)
file(GLOB_RECURSE ./monster MONSTER_SUB_SRC)

list(APPEND MODULE_SRC ${PLAYER_SUB_SRC} ${SAVE_GAME_SUB_SRC} ${MONSTER_SUB_SRC})

add_library(${MODULE_NAME} ${MODULE_SHARED_OR_STATIC})
target_sources(${MODULE_NAME} PRIVATE ${MODULE_SRC})
target_link_libraries(${MODULE_NAME} PRIVATE common client server)
target_include_directories(${MODULE_NAME} PUBLIC ${MODULE_INCLUDE_DIR})
