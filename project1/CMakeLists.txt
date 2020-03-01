cmake_minimum_required(VERSION 3.5.1)

project(project1 VERSION 1.0)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})

FIND_PACKAGE(PkgConfig REQUIRED)
PKG_CHECK_MODULES(GTK3 REQUIRED gtk+-3.0)

include_directories(${GTK3_INCLUDE_DIRS})
include_directories("${PROJECT_SOURCE_DIR}")

include_directories(
        ${PROJECT_SOURCE_DIR}/inc
        ${PROJECT_SOURCE_DIR}/src
)

file(GLOB SRC_LIST
        "${PROJECT_SOURCE_DIR}/src/inc/*.h"
	"${PROJECT_SOURCE_DIR}/src/*.c"
)

set(LIBRARIES ${GTK3_LIBRARIES})

add_executable(${PROJECT_NAME} ${SRC_LIST})

#линковка программы с библиотеками
target_link_libraries(${PROJECT_NAME} ${LIBRARIES})

