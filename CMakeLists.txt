cmake_minimum_required(VERSION 3.9)
project(Exe2.1)

file(GLOB_RECURSE Exe2.1_SRC src/*.cpp include/*.h)

include_directories(include/)
add_executable(Exe2.1 ${Exe2.1_SRC})
set(EXTERNAL_DIR ${CMAKE_SOURCE_DIR}/externals)



#SFML
set(SFML_DIR ${EXTERNAL_DIR}/SFML)
set(SFML_BUILD_EXAMPLES FALSE)
add_subdirectory(${SFML_DIR})
include_directories(${SFML_DIR}/include)

LIST(APPEND Exe2.1_LIBRARIES
	sfml-system
	sfml-window
	sfml-graphics
	sfml-audio
	sfml-network)
#Box2D
set(BOX2D_DIR ${EXTERNAL_DIR}/Box2D)

SET(BOX2D_INSTALL ON CACHE INTERNAL "")
SET(BOX2D_BUILD_STATIC ON  CACHE INTERNAL "")

add_subdirectory(${BOX2D_DIR})
include_directories(${BOX2D_DIR}/)
LIST(APPEND Exe2.1_LIBRARIES
	Box2D)
	
target_link_libraries(Exe2.1 ${Exe2.1_LIBRARIES})
	