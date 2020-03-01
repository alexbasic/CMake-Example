cmake_minimum_required(VERSION 3.5.1)

project(project1 VERSION 1.0)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/../cmake/")

include_directories(
        ${PROJECT_SOURCE_DIR}/inc
        ${PROJECT_SOURCE_DIR}/src
)

find_package(GTK3 REQUIRED COMPONENTS gtk)
include_directories(${GTK3_INCLUDE_DIR})
include_directories("${PROJECT_SOURCE_DIR}")

if(NOT GTK3_FOUND)
	message(FATAL_ERROR "GTK not found")
endif()

file(GLOB SRC_LIST
        "${PROJECT_SOURCE_DIR}/src/inc/*.h"
	"${PROJECT_SOURCE_DIR}/src/*.c"
)

set(LIBRARIES ${GTK3_LIBRARIES})

add_executable(${PROJECT_NAME} ${SRC_LIST})

#линковка программы с библиотеками
target_link_libraries(${PROJECT_NAME} ${LIBRARIES})

