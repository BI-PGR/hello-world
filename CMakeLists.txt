cmake_minimum_required (VERSION 3.1)

project(hello-world)

add_subdirectory (pgr-framework)

add_executable(${PROJECT_NAME} hello-world.cpp)

target_link_libraries(${PROJECT_NAME} pgr)
