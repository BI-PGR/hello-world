cmake_minimum_required(VERSION 3.0)

project(hello-world)

# Find pgr-framework
string(ASCII 27 Esc)
set(RED "${Esc}[31;1m")
set(RST "${Esc}[m")

if(NOT EXISTS "${CMAKE_CURRENT_SOURCE_DIR}/../pgr-framework")
  message(FATAL_ERROR
  "${RED}Failed to find ../pgr-framework${RST}, fetch the repo using\n"
  "\tgit clone https://github.com/bi-pgr/pgr-framewor\n"
  "next to the folder containing this project.")
endif()

add_subdirectory(
  "${CMAKE_CURRENT_SOURCE_DIR}/../pgr-framework"
  "pgr-framework"
)

# Silence deprecated GLUT functions
if(APPLE)
  add_definitions(-Wno-deprecated)
endif()

# Set up targets
add_executable(${PROJECT_NAME} hello-world.cpp)

target_link_libraries(${PROJECT_NAME} pgr)
