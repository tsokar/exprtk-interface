PROJECT(exprtk)
cmake_minimum_required(VERSION 2.8)

include(cmake/add_dependency.cmake)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake ${CMAKE_CURRENT_SOURCE_DIR}/cmake/Modules)

set(${PROJECT_NAME}_MAJOR_VERSION 01)
set(${PROJECT_NAME}_MINOR_VERSION 00)
set(${PROJECT_NAME}_PATCH_VERSION 00)
include(cmake/set_version_numbers.cmake)

# header-only library
add_library(${PROJECT_NAME} INTERFACE)

# Install the library and the executables
install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/exprtk/exprtk.hpp" DESTINATION include )

set(${PROJECT_NAME}_INCLUDE_DIRS "${CMAKE_INSTALL_PREFIX}/include")
set(${PROJECT_NAME}_LIBRARIES "")
set(${PROJECT_NAME}_LIBRARY_DIRS "")
set(${PROJECT_NAME}_CXX_FLAGS "")
set(${PROJECT_NAME}_LINK_FLAGS "")
include(${CMAKE_SOURCE_DIR}/cmake/create_cmake_config_files.cmake)

#doxygen seems to hang forever. Deactivated for the moment
#include(cmake/enable_doxygen_documentation.cmake)
