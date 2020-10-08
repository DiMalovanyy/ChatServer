

#add permission to use all headers that use main executable
include_directories(${CMAKE_BINARY_DIR})

#create executable for testing project
add_executable(${CMAKE_PROJECT_NAME}_test main.cpp)

#link the google test library
target_link_libraries(${CMAKE_PROJECT_NAME}_test gtest)
