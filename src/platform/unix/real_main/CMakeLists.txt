set(MODULE_NAME "quake2")

set(MODULE_INCLUDE_DIR "${CMAKE_SOURCE_DIR}/include")

set(MODULE_SRC "${CMAKE_CURRENT_SOURCE_DIR}/main.c")

add_executable(${MODULE_NAME})

set_target_properties(${MODULE_NAME} PROPERTIES 
  LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}
  RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

target_sources(${MODULE_NAME} PRIVATE ${MODULE_SRC})
target_link_libraries(${MODULE_NAME} PRIVATE unix ${yquake2LinkerFlags})
target_include_directories(${MODULE_NAME} PUBLIC ${MODULE_INCLUDE_DIR})
