cmake_minimum_required(VERSION 3.9)

set(PUBLIC_HEADERS 
  
  src/lib/rply.h 
  src/lib/rplyfile.h  
)
set(PROJECT_SRCS
  src/tools/convert.c
  src/tools/create_ply.c
  src/tools/dump.c
  src/tools/sconvert.c
  src/lib/rply.c
)

set(PUBLIC_HEADER_PATH "${CMAKE_SOURCE_DIR}/librply/src/lib")

#######################
set(librply "librply")
add_library(${librply} STATIC "${PROJECT_SRCS}" "${PUBLIC_HEADERS}")
target_include_directories(${librply} PUBLIC ${PUBLIC_HEADER_PATH})
target_include_directories(${librply} PUBLIC ${CMAKE_SOURCE_DIR})
set_target_properties(${librply} PROPERTIES FOLDER ${librply})
source_group("Source Files" FILES ${PROJECT_SRCS})
source_group("Public Headers" FILES ${PUBLIC_HEADERS})

