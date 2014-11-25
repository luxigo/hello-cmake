cmake_minimum_required (VERSION 2.8)

# set installation prefix
if (NOT DEFINED CMAKE_INSTALL_PREFIX)
  set(CMAKE_INSTALL_PREFIX /usr/local CACHE STRING "Set installation prefix")
endif (NOT DEFINED CMAKE_INSTALL_PREFIX)

# set build type
if (NOT DEFINED CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug CACHE STRING "Set build type" FORCE)
endif (NOT DEFINED CMAKE_BUILD_TYPE)

# set project name
project (hello_cmake)

# install mainscript.sh
install(FILES
  src/mainscript.sh
  DESTINATION ${CMAKE_INSTALL_PREFIX}/bin)

# declare subdirectories
set(SUBPROJECT_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/subproject)
add_subdirectory(${SUBPROJECT_SOURCE_DIR})

# declare uninstall target
# (only in top directory, where cmake_uninstall.cmake.in must reside)
configure_file(
    "${CMAKE_CURRENT_SOURCE_DIR}/cmake_uninstall.cmake.in"
    "${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake"
    IMMEDIATE @ONLY)
add_custom_target(uninstall
    COMMAND ${CMAKE_COMMAND} -P ${CMAKE_CURRENT_BINARY_DIR}/cmake_uninstall.cmake)
