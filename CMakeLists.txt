cmake_minimum_required(VERSION 3.15)

project(queue C)

set(C_STANDARD 11)

include(cmake/CompilerWarnings.cmake)
add_library(project_warnings INTERFACE)
add_library(utils::warnings ALIAS project_warnings)
set_project_warnings(project_warnings)

include(cmake/EnableTests.cmake)
include(cmake/BuildType.cmake)

include(cmake/Sanitizers.cmake)
add_library(sanitizers INTERFACE)
add_library(utils::sanitizers ALIAS sanitizers)
set_sanitizers(sanitizers)

add_library(queue)

target_sources(queue PRIVATE
    src/queue.c
)

target_include_directories(queue PUBLIC ${CMAKE_SOURCE_DIR}/include)

target_link_libraries(queue
    PRIVATE project_warnings sanitizers
)