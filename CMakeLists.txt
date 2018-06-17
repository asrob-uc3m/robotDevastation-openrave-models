# Authors: see AUTHORS.md at project root.
# CopyPolicy: released under the terms of the LGPLv2.1, see LICENSE at project root.
# URL: https://github.com/asrob-uc3m/robotDevastation

cmake_minimum_required(VERSION 3.0 FATAL_ERROR)

# Define a project.
project(RD_OPENRAVE_MODELS LANGUAGES NONE)

# Find hard dependencies.
find_package(YCM REQUIRED)
find_package(YARP REQUIRED)

if(YARP_VERSION_SHORT VERSION_LESS 2.3.70)
    list(APPEND CMAKE_MODULE_PATH ${YARP_MODULE_PATH})
    include(YarpInstallationHelpers)
endif()

# Set some useful variables.
yarp_configure_external_installation(robotDevastation-openrave-models)

# Install stuff.
install(DIRECTORY openrave
        DESTINATION ${ROBOTDEVASTATION-OPENRAVE-MODELS_CONTEXTS_INSTALL_DIR})

# Store this package in the user registry.
export(PACKAGE ${PROJECT_NAME})

# Define CMAKE_INSTALL_<dir> and CMAKE_INSTALL_FULL_<dir> variables.
include(GNUInstallDirs)

# Set installation path for CMake files.
if(WIN32)
    set(${PROJECT_NAME}_CMAKE_DESTINATION "CMake")
else()
    set(${PROJECT_NAME}_CMAKE_DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}")
endif()

# Create dummy CMake configuration export file.
file(WRITE ${CMAKE_BINARY_DIR}/${PROJECT_NAME}Config.cmake "# Dummy CMake configuration export file.")

# Install CMake configuration file.
install(FILES ${CMAKE_BINARY_DIR}/${PROJECT_NAME}Config.cmake
        DESTINATION ${${PROJECT_NAME}_CMAKE_DESTINATION})

# Add uninstall rule.
include(AddUninstallTarget)
