cmake_minimum_required(VERSION 3.24)
project(project_name)

set(CMAKE_CXX_STANDARD 14)

add_executable(${PROJECT_NAME} main.cpp)

# Find packages for gl rendering
find_package(glfw3 3.3 REQUIRED)
find_package(GLEW REQUIRED)
find_package(OpenGL REQUIRED)

# Link found libraries to target project
# The libraries are install on the system with package manager like brew
# If not, should install the libraries following manually.
target_link_libraries(${PROJECT_NAME} glfw)
target_link_libraries(${PROJECT_NAME} GLEW::GLEW)
target_link_libraries(${PROJECT_NAME} OpenGL::GL)

# Include manually included libraries
# glad library would differ by computing systems.
include_directories(libs/glad/include)
add_library(glad libs/glad/src/glad.c)

# Link manually included libraries to target project
target_link_libraries(${PROJECT_NAME} glad)