cmake_minimum_required (VERSION 2.8)

if (NOT DEFINED CMAKE_INSTALL_PREFIX)
  set(CMAKE_INSTALL_PREFIX /usr/local CACHE STRING "Set installation prefix")
endif (NOT DEFINED CMAKE_INSTALL_PREFIX)

project (subproject)

if (NOT DEFINED CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug CACHE STRING "Set build type" FORCE)
endif(NOT DEFINED CMAKE_BUILD_TYPE)

# install scripts
install(FILES
  src/subscript.sh
  DESTINATION ${CMAKE_INSTALL_PREFIX}/bin)
