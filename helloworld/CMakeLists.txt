cmake_minimum_required(VERSION 3.13)

project(helloworld)

# 根据自己路径修改
# set(CMAKE_MODULE_PATH "~/workspace/C++/netplus/projects/cmake/modules")
set(CMAKE_MODULE_PATH "D:/workspace/C++/netplus/projects/cmake/modules")

add_executable(${PROJECT_NAME} main.cpp)
find_package(netplus REQUIRED)

if(netplus_FOUND)
    message (STATUS "netplus found")
	# include_directories(${netplus_INCLUDE_DIR})
	include_directories(${netplus_INCLUDE_DIR})
	# target_link_libraries(${PROJECT_NAME} ${netplus_LIBRARY})
	target_link_libraries(${PROJECT_NAME} ${netplus_LIBRARY})
	if (NOT WIN32)
	  TARGET_LINK_LIBRARIES(${PROJECT_NAME} dl)
	  TARGET_LINK_LIBRARIES(${PROJECT_NAME} pthread)
	endif (NOT WIN32)
else()
    message (FATAL_ERROR "Couldn't found netplus")
endif(netplus_FOUND)
