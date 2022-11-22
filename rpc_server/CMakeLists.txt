cmake_minimum_required(VERSION 3.22)
project(rpc_server)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++11")

SET(ENABLE_SSL OFF)

if (ENABLE_SSL)
    add_definitions(-DCINATRA_ENABLE_SSL)
    message(STATUS "Use SSL")
endif()

set(OpenCV_DIR D://workplace//library//opencv-4.6.0//build//install)
find_package(OpenCV 4.0 REQUIRED)
find_package(Boost COMPONENTS system filesystem REQUIRED)

include_directories(
        ${OpenCV_INCLUDE_DIRS}
        "/usr/local/include"
        "./include"
        "./thirdparty/msgpack-c/include")

add_executable(rpc_server main.cpp util_serialization.h)

target_link_libraries(rpc_server ${OpenCV_LIBS})

if (ENABLE_SSL)
    target_link_libraries(rpc_server ${Boost_LIBRARIES} -lssl -lcrypto -lpthread)
else()
    target_link_libraries(rpc_server ${Boost_LIBRARIES})
endif()
