PROJECT(exprtk)
cmake_minimum_required(VERSION 3.16)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake ${CMAKE_CURRENT_SOURCE_DIR}/cmake/Modules)

set(${PROJECT_NAME}_MAJOR_VERSION 01)
set(${PROJECT_NAME}_MINOR_VERSION 04)
set(${PROJECT_NAME}_PATCH_VERSION 00)
include(cmake/set_version_numbers.cmake)

# header-only library
add_library(${PROJECT_NAME} INTERFACE)

# let cmake target know where includes will be
target_include_directories(${PROJECT_NAME} INTERFACE
    "$<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/exprtk>"
    # relative to ${CMAKE_INSTALL_PREFIX} but don't explicitly mention it
    "$<INSTALL_INTERFACE:include>")

# Install the library and the executables, and cmake-config
install( TARGETS ${PROJECT_NAME}
         EXPORT ${PROJECT_NAME}Targets)

install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/exprtk/exprtk.hpp" DESTINATION include )

set(PROVIDES_EXPORTED_TARGETS 1)
include(${CMAKE_SOURCE_DIR}/cmake/create_cmake_config_files.cmake)
