cmake_minimum_required(VERSION 3.5)

project(Game LANGUAGES CXX)

find_library(EE REQUIRED)

if(NOT ${EE_FOUND})
    message(FATAL_ERROR "NO Emerald engine")
endif()

add_executable(${PROJECT_NAME}_test test.cpp)

target_link_libraries(${PROJECT_NAME}_test ${EE_LIBRARIES})
target_include_directories(${PROJECT_NAME}_test PRIVATE ${EE_INCLUDE_DIRS})

set_target_properties(${PROJECT_NAME}_test PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)
