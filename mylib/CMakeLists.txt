cmake_minimum_required(VERSION 3.10.2)
project(mylib)

##################################################################
# Require c++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)


# Add warnings
add_compile_options("-Wall")
add_compile_options("-Wextra")
add_compile_options("-Wpedantic")
add_compile_options("-Werror")


# Files
string(TOLOWER "${PROJECT_NAME}" LIB_NAME)
set(SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/mylib.cpp)
set(INCLUDES
    ${CMAKE_CURRENT_SOURCE_DIR}/include)
set(LIBRARY_OUTPUT_PATH ${MYLIB_LIB_OUT_PATH})


##################################################################
# BUILD LIBRARY
add_library(${LIB_NAME} SHARED "")
target_sources(${LIB_NAME} PRIVATE ${SOURCES})
target_include_directories(${LIB_NAME} PRIVATE ${INCLUDES})