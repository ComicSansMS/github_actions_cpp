cmake_minimum_required(VERSION 3.20)

project(github_actions_demo CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_compile_options($<$<CXX_COMPILER_ID:MSVC>:/W4>)
add_compile_options($<$<CXX_COMPILER_ID:MSVC>:/permissive->)
add_compile_options($<$<CXX_COMPILER_ID:MSVC>:/std:c++latest>)

add_executable(demo demo.cpp)

add_custom_target(run_demo
                  COMMAND demo.exe
                  DEPENDS demo
                  WORKING_DIRECTORY ${PROJECT_BINARY_DIR}/$<CONFIG>
                  )