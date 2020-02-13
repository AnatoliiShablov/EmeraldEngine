cmake_minimum_required(VERSION 3.5)

project(EmeraldEngine LANGUAGES CXX)

find_package(SDL2 QUIET) # у меня нет, поэтому поменял

set(EE_WORLD ${PROJECT_NAME}_world)
add_library(${EE_WORLD} include/world.hpp src/world.cpp)

target_include_directories(${EE_WORLD} PUBLIC include)

target_include_directories(${EE_WORLD} PRIVATE ${SDL2_INCLUDE_DIRS})
target_link_libraries(${EE_WORLD} ${SDL2_LIBRARIES})

set(EE_MAIN ${PROJECT_NAME}_main)
add_library(${EE_MAIN} include/EE.hpp src/EE.cpp)
add_library(EE ALIAS ${EE_MAIN})

target_include_directories(${EE_MAIN} PUBLIC include)
target_link_libraries(${EE_MAIN} ${EE_WORLD})