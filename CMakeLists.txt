cmake_minimum_required(VERSION 2.8)
project(libnetfilter_conntrack)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

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
