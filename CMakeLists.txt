cmake_minimum_required(VERSION 3.17.3)

set(PROJECT_NAME CppDecoratorDesignPattern)
project(${PROJECT_NAME})

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++20 -pthread")
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} /usr/lib/x86_64-linux-gnu/cmake/gnuradio/ ~/intel/ipp)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} /)

set(BOOST_REQUIRED_COMPONENTS
        system
        thread
        regex
        coroutine
        context
        filesystem
        date_time
        )

find_package(Boost "1.73.0" REQUIRED ${BOOST_REQUIRED_COMPONENTS})
include_directories(SYSTEM ${Boost_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS})

file(GLOB_RECURSE SOURCES RELATIVE ${CMAKE_SOURCE_DIR} "src/*")
add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES})