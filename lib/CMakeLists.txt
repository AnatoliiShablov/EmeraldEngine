cmake_minimum_required(VERSION 3.5)

project(EmeraldEngine LANGUAGES CXX)

find_package(SDL2 REQUIRED)

set(EE_WORLD ${PROJECT_NAME}_world)
add_library(${EE_WORLD} include/world.hpp src/world.cpp)
add_library(EE::World ALIAS ${EE_WORLD})

target_include_directories(${EE_WORLD} PRIVATE include/)

target_include_directories(${EE_WORLD} PRIVATE ${SDL2_INCLUDE_DIRS})
target_link_libraries(${EE_WORLD} ${SDL2_LIBRARIES})

set_target_properties(${EE_WORLD} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)

set(EE_MAIN ${PROJECT_NAME}_main)
add_library(${EE_MAIN} include/EE.hpp src/EE.cpp)
add_library(EE ALIAS ${EE_MAIN})

target_include_directories(${EE_MAIN} PRIVATE include/)
target_link_libraries(${EE_MAIN} ${EE_WORLD})

set_target_properties(${EE_MAIN} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)


set(EE_LIBRARIES ${EE_MAIN} ${EE_WORLD})
set(EE_INCLUDE_DIRS include/)
set(EE_FOUND TRUE)
