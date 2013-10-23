cmake_minimum_required(VERSION 2.8)
project(libnetfilter_conntrack)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
# use, i.e. don't skip the full RPATH for the build tree
SET(CMAKE_SKIP_BUILD_RPATH  FALSE)

# when building, don't use the install RPATH already
# (but later on when installing)
SET(CMAKE_BUILD_WITH_INSTALL_RPATH FALSE) 

SET(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib")

# add the automatically determined parts of the RPATH
# which point to directories outside the build tree to the install RPATH
SET(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)


# the RPATH to be used when installing, but only if it's not a system directory
LIST(FIND CMAKE_PLATFORM_IMPLICIT_LINK_DIRECTORIES "${CMAKE_INSTALL_PREFIX}/lib" isSystemDir)
IF("${isSystemDir}" STREQUAL "-1")
   SET(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib")
ENDIF("${isSystemDir}" STREQUAL "-1")

find_package(LibMNL REQUIRED)
find_package(Libnfnetlink REQUIRED)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/include
	${MNL_INCLUDE_DIR}
	${NFNETLINK_INCLUDE_DIR}
)

link_directories(${TSAGENT_DEPS_INSTALL}/lib)

add_subdirectory(src)
add_subdirectory(include)
