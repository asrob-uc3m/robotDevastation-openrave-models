# Copyright: 2014 UC3M
# Author: Juan G Victores
# CopyPolicy: Released under the terms of the GNU GPL v2.0.

set(appname openrave)

find_package(YARP REQUIRED)

list(APPEND CMAKE_MODULE_PATH ${YARP_MODULE_PATH})
include(YarpInstallationHelpers)
yarp_configure_external_installation(robotDevastation-openrave-models)

#yarp_install(FILES ymanager.ini DESTINATION ${RD_OPENRAVE_MODELS_DATA_INSTALL_DIR})  # Cleaner than ${RD_OPENRAVE_MODELS_ROBOTS_INSTALL_DIR}/../ or similar.

file(GLOB ecro ${CMAKE_CURRENT_SOURCE_DIR}/ecro/*.xml)
file(GLOB ecro/models ${CMAKE_CURRENT_SOURCE_DIR}/ecro/models/*.wrl)

yarp_install(FILES ${ecro} DESTINATION ${ROBOTDEVASTATION-OPENRAVE-MODELS_CONTEXTS_INSTALL_DIR}/${appname}/ecro)
yarp_install(FILES ${ecro/models} DESTINATION ${ROBOTDEVASTATION-OPENRAVE-MODELS_CONTEXTS_INSTALL_DIR}/${appname}/ecro/models)

