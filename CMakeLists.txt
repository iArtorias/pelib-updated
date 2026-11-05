cmake_minimum_required(VERSION 3.15)

project(pelib CXX)

# Default build type for single configuration generators
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
	message(STATUS "Setting build type to 'Release' as none was specified.")
	set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Choose the type of build." FORCE)
endif()

# Install rules only when PeLib is the top level project, a parent project ('FetchContent', 'add_subdirectory') decides itself
if(CMAKE_SOURCE_DIR STREQUAL PROJECT_SOURCE_DIR)
	set(PELIB_INSTALL_DEFAULT ON)
else()
	set(PELIB_INSTALL_DEFAULT OFF)
endif()

option(PELIB_INSTALL "Generate the install target" ${PELIB_INSTALL_DEFAULT})

add_subdirectory(src)