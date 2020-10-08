#set the last stable version for this project
cmake_minimum_required(VERSION 3.5)

#setup project name and version (Major, minor, Patch)
project(ChatServer VERSION 0.0.1)

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

#deligate work for subdirectory
add_subdirectory(test)
add_subdirectory(lib/googletest) #https://github.com/google/googletest
