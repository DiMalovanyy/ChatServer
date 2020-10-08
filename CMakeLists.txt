#set the last stable version for this project
cmake_minimum_required(VERSION 3.5)

#setup project name and version (Major, minor, Patch)
project(ChatServer VERSION 0.0.1)

#find boost library
find_package(Boost REQUIRED)
if (NOT Boost_FOUND)
	message(FATAL "cmake can't found boost library")
endif()

#include all boost headers and sources and other components
include_directories(${Boost_INCLUDE_DIRS})

#set variables for Headers and sources files
set(HEADERS 
	chat_message.h
	)

set(SOURCES
	chat_client.cpp
	chat_server.cpp
	)


#compile all headers and sources in binary file
add_executable(${CMAKE_PROJECT_NAME}_bin ${HEADERS} ${SOURCES})

#add some properties to executable
set_target_properties(
                    ${CMAKE_PROJECT_NAME}_bin PROPERTIES
                    CXX_STANDARD 17
                    CXX_STANDARD_REQUIRED ON
)

#deligate work for subdirectory
add_subdirectory(test)
add_subdirectory(lib/googletest) #https://github.com/google/googletest

#show to the linker where the boost libraries located
target_link_libraries(${CMAKE_PROJECT_NAME}_bin LINK_PUBLIC ${Boost_LIBRARIES})
