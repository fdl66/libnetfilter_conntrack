cmake_minimum_required(VERSION 2.8)
project(libnetfilter_conntrack)

message("hi ${CMAKE_INSTALL_PREFIX}")
set(CMAKE_SKIP_BUILD_RPATH FALSE)
set(CMAKE_BUILD_WITH_INSTALL_RPATH FALSE)
set(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib")
set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE)

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
