cmake_minimum_required(VERSION 3.5)

project(EmeraldEngine LANGUAGES CXX)

find_package(SDL2 REQUIRED)

set(EE_WORLD ${PROJECT_NAME}_world)
add_library(${EE_WORLD} include/world.hpp src/world.cpp)

target_include_directories(${EE_WORLD} PUBLIC include/ PRIVATE ${SDL2_INCLUDE_DIRS})
target_link_libraries(${EE_WORLD} ${SDL2_LIBRARIES})

set_target_properties(${EE_WORLD} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)

set(EE_MAIN ${PROJECT_NAME}_main)
add_library(${EE_MAIN} include/EE.hpp src/EE.cpp)
add_library(EE ALIAS ${EE_MAIN})

target_include_directories(${EE_MAIN} PUBLIC include/)
target_link_libraries(${EE_MAIN} ${EE_WORLD})

set_target_properties(${EE_MAIN} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)


set(EE_LIBRARIES EE PARENT_SCOPE)
set(EE_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}/include/ PARENT_SCOPE)
set(EE_FOUND TRUE PARENT_SCOPE)
