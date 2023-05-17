cmake_minimum_required(VERSION 3.18)


find_package(libfmt REQUIRED)


project(mylib)


file(GLOB_RECURSE 
    my_headers
    ${CMAKE_CURRENT_SOURCE_DIR}/include/*.hpp)
aux_source_directory(
    ${CMAKE_CURRENT_SOURCE_DIR}/sources
    my_sources)


add_library(${PROJECT_NAME} STATIC 
    ${my_headers} ${my_sources})

#  |
#  |  ??
#  V
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

target_link_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>)

target_link_libraries(
    ${PROJECT_NAME} PUBLIC
    fmt::fmt)


install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION lib)



