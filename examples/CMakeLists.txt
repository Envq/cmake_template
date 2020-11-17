cmake_minimum_required(VERSION 3.10.2)
project(examples)

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


# FILES
string(TOLOWER "example.x" BIN_NAME)
set(EXECUTABLE_OUTPUT_PATH ${MYLIB_BIN_OUT_PATH})
set(INCLUDES
    ${CMAKE_SOURCE_DIR}/mylib/include)


##################################################################
# BUILD EXECUTABLE
add_executable(${BIN_NAME} ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp)
target_include_directories(${BIN_NAME} PRIVATE ${INCLUDES})
target_link_libraries(${BIN_NAME} mylib)