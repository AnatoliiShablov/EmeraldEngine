cmake_minimum_required(VERSION 3.5)

project(Game LANGUAGES CXX)

find_library(EE REQUIRED)

if(NOT ${EE_FOUND})
    message(FATAL_ERROR "No Emerald engine")
endif()

add_executable(${PROJECT_NAME}_test test.cpp)

target_link_libraries(${PROJECT_NAME}_test EE)