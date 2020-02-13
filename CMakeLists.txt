cmake_minimum_required(VERSION 3.5)

project(EmeraldEngine LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CXX_EXTENSIONS NO)

add_subdirectory(lib)
add_subdirectory(src)
