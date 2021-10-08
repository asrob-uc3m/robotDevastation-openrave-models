# Authors: see AUTHORS.md at project root.
# CopyPolicy: released under the terms of the LGPLv2.1, see LICENSE at project root.
# URL: https://github.com/asrob-uc3m/robotDevastation

cmake_minimum_required(VERSION 3.12)

# Define a project.
project(RD_OPENRAVE_MODELS LANGUAGES NONE)

# Find dependencies
find_package(YCM 0.11 REQUIRED)
find_package(YARP 3.2 REQUIRED)

# Set some useful variables - paths relative to the installation prefix.
yarp_configure_external_installation(robotDevastation-openrave-models)

# Configure install rule, copy models to the build directory.
yarp_install(DIRECTORY openrave
             DESTINATION ${ROBOTDEVASTATION-OPENRAVE-MODELS_DATA_INSTALL_DIR})

# Store this package in the user registry.
set(CMAKE_EXPORT_PACKAGE_REGISTRY ON)

# Create and install config files.
include(InstallBasicPackageFiles)

install_basic_package_files(RD_OPENRAVE_MODELS
                            VERSION 0.1.0
                            COMPATIBILITY AnyNewerVersion
                            NO_EXPORT)

# Add uninstall rule.
include(AddUninstallTarget)
