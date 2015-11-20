cmake_minimum_required(VERSION 2.8)
project(aruco)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

################################################################################
#PACKAGES
find_package(OpenCV REQUIRED)
################################################################################
#INCLUDES
include_directories(include)
################################################################################
#SOURCES
file(GLOB ARUCO_SOURCES "src/*.cpp")
file(GLOB ARUCO_SAMPLES "samples/*.cpp")
################################################################################
#LINK
LIST(APPEND LINK_LIBS ${OpenCV_LIBS})
################################################################################
#EXECUTABLES
foreach(SAMPLE ${ARUCO_SAMPLES})
	get_filename_component(EXEC_NAME ${SAMPLE} NAME_WE)
	add_executable(${EXEC_NAME} ${ARUCO_SOURCES} ${SAMPLE})
	target_link_libraries(${EXEC_NAME} ${LINK_LIBS})
endforeach(SAMPLE)
################################################################################
