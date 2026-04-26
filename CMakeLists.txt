
cmake_minimum_required(VERSION 3.20)

project("generated_code")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)

# Find requirements
find_package(fastcdr REQUIRED)
find_package(fastdds 3 REQUIRED)


message(STATUS "Configuring HelloWorld...")
add_library(HelloWorld_lib HelloWorldTypeObjectSupport.cxx HelloWorldPubSubTypes.cxx)
target_link_libraries(HelloWorld_lib fastcdr fastdds)

add_executable(HelloWorld HelloWorldApplication.cxx HelloWorldPublisherApp.cxx HelloWorldSubscriberApp.cxx HelloWorldmain.cxx)
target_link_libraries(HelloWorld fastcdr fastdds
        HelloWorld_lib 
        )



