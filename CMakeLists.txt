cmake_minimum_required(VERSION 3.30)

project(xbox-swizzle)

# Texture swizzling routines.
add_library(
        ${PROJECT_NAME}
        src/xbox-swizzle/swizzle.c
        src/xbox-swizzle/swizzle.h
)

target_include_directories(
        ${PROJECT_NAME}
        PUBLIC
        "${CMAKE_CURRENT_SOURCE_DIR}/src"
)
