set(MODULE_NAME "soft")
set(MODULE_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")

set(MODULE_SRC)
aux_source_directory(. MODULE_SRC)

set(FILES_SRC)
aux_source_directory(../files/ FILES_SRC)

list(APPEND MODULE_SRC ${FILES_SRC})

add_library(${MODULE_NAME} SHARED)
set_target_properties(${MODULE_NAME} PROPERTIES 
  PREFIX ""
  OUTPUT_NAME "ref_${MODULE_NAME}"
  SUFFIX ${CMAKE_SHARED_LIBRARY_SUFFIX}
  LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

target_sources(${MODULE_NAME} PRIVATE ${MODULE_SRC})
target_link_libraries(${MODULE_NAME} PRIVATE common client unix game server)
target_include_directories(${MODULE_NAME} PUBLIC ${MODULE_INCLUDE_DIR})


