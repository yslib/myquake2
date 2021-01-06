
list(APPEND yquake2LinkerFlags "-lm")
list(APPEND yquake2LinkerFlags ${CMAKE_DL_LIBS})



if(${CMAKE_SYSTEM_NAME} MATCHES "Windows")
	list(APPEND yquake2LinkerFlags "-lws2_32 -lwinmm -static-libgcc")
else()
	if (NOT ${CMAKE_SYSTEM_NAME} MATCHES "Haiku")
		list(APPEND yquake2LinkerFlags "-rdynamic")
	else()
		list(APPEND yquake2LinkerFlags "-lnetwork")
	endif()
endif()

if(NOT ${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
	if(NOT ${CMAKE_SYSTEM_NAME} MATCHES "OpenBSD")
		list(APPEND yquake2LinkerFlags "-Wl,--no-undefined")
	endif()
endif()

if(${CMAKE_SYSTEM_NAME} MATCHES "Windows")
  
  # TODO
else()
  add_subdirectory(unix)
endif()
