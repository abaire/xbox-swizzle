cmake_minimum_required(VERSION 3.30)

project(xbox-swizzle VERSION 1.0.0 LANGUAGES C)

# Texture swizzling routines.
add_library(
        ${PROJECT_NAME}
        src/xbox-swizzle/swizzle.c
        src/xbox-swizzle/swizzle.h
)

include(GNUInstallDirs)
include(CMakePackageConfigHelpers)

install(
        TARGETS
        ${PROJECT_NAME}
        EXPORT XboxSwizzleTargets
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)

write_basic_package_version_file(
        "${CMAKE_CURRENT_BINARY_DIR}/XboxSwizzleConfigVersion.cmake"
        VERSION ${PROJECT_VERSION}
        COMPATIBILITY AnyNewerVersion
)

configure_package_config_file(
        "cmake/XboxSwizzleConfig.cmake.in" # You will need to create this file
        "${CMAKE_CURRENT_BINARY_DIR}/XboxSwizzleConfig.cmake"
        INSTALL_DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}
)

install(
        EXPORT XboxSwizzleTargets
        FILE XboxSwizzleTargets.cmake
        NAMESPACE XboxSwizzle::
        DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}
)

install(
        FILES
        "${CMAKE_CURRENT_BINARY_DIR}/XboxSwizzleConfig.cmake"
        "${CMAKE_CURRENT_BINARY_DIR}/XboxSwizzleConfigVersion.cmake"
        DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}
)
