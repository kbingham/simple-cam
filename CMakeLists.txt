cmake_minimum_required(VERSION 3.6)

project(SimpleCam
	DESCRIPTION "A small and documented example application for libcamera"
	LANGUAGES CXX)

set (CMAKE_CXX_STANDARD 17)
set (CMAKE_CXX_FLAGS "-Wall -Winvalid-pch -Wnon-virtual-dtor -Wextra -Werror -Wno-unused-parameter")

find_package(PkgConfig)
find_package(OpenCV REQUIRED)

pkg_check_modules(LIBCAMERA REQUIRED IMPORTED_TARGET libcamera)
pkg_check_modules(LIBEVENT REQUIRED IMPORTED_TARGET libevent_pthreads)

message(STATUS "libcamera library found:")
message(STATUS "    version: ${LIBCAMERA_VERSION}")
message(STATUS "    libraries: ${LIBCAMERA_LINK_LIBRARIES}")
message(STATUS "    include path: ${LIBCAMERA_INCLUDE_DIRS}")

message(STATUS "libevent_pthreads library found:")
message(STATUS "    version: ${LIBEVENT_VERSION}")
message(STATUS "    libraries: ${LIBEVENT_LINK_LIBRARIES}")
message(STATUS "    include path: ${LIBEVENT_INCLUDE_DIRS}")

include_directories(${CMAKE_SOURCE_DIR} ${LIBCAMERA_INCLUDE_DIRS} ${LIBEVENT_INCLUDE_DIRS} ${OpenCV_INCLUDE_DIRS})

add_executable(simple-cam simple-cam.cpp event_loop.cpp)

target_link_libraries(simple-cam
                      PkgConfig::LIBEVENT
                      PkgConfig::LIBCAMERA
                      ${OpenCV_LIBS})
