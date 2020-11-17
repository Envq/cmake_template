cmake_minimum_required(VERSION 3.10.2)
project(foo)


##################################################################
# FILES
SET(MYLIB_LIB_OUT_PATH ${PROJECT_SOURCE_DIR}/lib)
SET(MYLIB_BIN_OUT_PATH ${PROJECT_SOURCE_DIR}/bin)

add_subdirectory(mylib)
add_subdirectory(examples)


##################################################################
# CLEAN COMMAND
add_custom_target(rm
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/build/*
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/doc
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/bin
    COMMAND rm -rf ${PROJECT_SOURCE_DIR}/lib
    COMMENT "Clean build, bin and doc directory")