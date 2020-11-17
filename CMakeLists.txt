cmake_minimum_required(VERSION 3.10.2)
project(foo)

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
string(TOLOWER "${PROJECT_NAME}.x" EXE_NAME)
string(TOLOWER "${PROJECT_NAME}" LIB_NAME)
set(SOURCES
    ${PROJECT_SOURCE_DIR}/src/mylib.cpp)
set(INCLUDES
    ${PROJECT_SOURCE_DIR}/include)
set(LIBRERIES
    ${PROJECT_SOURCE_DIR}/lib/lib${LIB_NAME}.so)


##################################################################
# BUILD LIBRARY
if (MODE STREQUAL 1)
    add_library(${LIB_NAME} SHARED "")
    target_sources(${LIB_NAME} PRIVATE ${SOURCES})
    target_include_directories(${LIB_NAME} PRIVATE ${INCLUDES})
endif()


##################################################################
# BUILD EXECUTABLE
if (MODE STREQUAL 2)
    add_executable(${EXE_NAME} ${PROJECT_SOURCE_DIR}/main.cpp)
    target_include_directories(${EXE_NAME} PRIVATE ${INCLUDES})
    target_link_libraries(${EXE_NAME} ${LIBRERIES})
endif()


##################################################################
# INSTALL COMMAND
if (MODE STREQUAL 1)
    install(TARGETS ${LIB_NAME} 
        DESTINATION ${PROJECT_SOURCE_DIR}/lib)
elseif (MODE STREQUAL 2)
    install(TARGETS ${EXE_NAME} 
        DESTINATION ${PROJECT_SOURCE_DIR}/bin)
endif()

##################################################################
# CLEAN COMMAND
add_custom_target(rm
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/build/*
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/doc
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/bin
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/lib
    COMMENT "Clean build, bin and doc directory")