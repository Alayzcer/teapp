cmake_minimum_required(VERSION 3.18)


project(myapp)


file(GLOB_RECURSE 
    my_headers
    ${CMAKE_CURRENT_SOURCE_DIR}/include/*.hpp)


aux_source_directory(
    ${CMAKE_CURRENT_SOURCE_DIR}/sources
    my_sources)


add_executable(${PROJECT_NAME}
    ${my_headers} ${my_sources})

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
target_link_directories(${PROJECT_NAME} PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>)


install(TARGETS ${PROJECT_NAME} DESTINATION bin)



