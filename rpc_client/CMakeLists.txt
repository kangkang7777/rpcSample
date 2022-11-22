cmake_minimum_required(VERSION 3.22)
project(rpc_client)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -std=c++11")

SET(ENABLE_SSL OFF)

if (ENABLE_SSL)
    add_definitions(-DCINATRA_ENABLE_SSL)
    message(STATUS "Use SSL")
endif()

set(OpenCV_DIR D://workplace//library//opencv-4.6.0//build//install)
find_package(Boost COMPONENTS system filesystem REQUIRED)
find_package(OpenCV 4.0 REQUIRED)

include_directories(
        ${OpenCV_INCLUDE_DIRS}
        "/usr/local/include"
        "./include"
        "./thirdparty/msgpack-c/include")

add_executable(client main.cpp)

target_link_libraries(client ${OpenCV_LIBS})

if (ENABLE_SSL)
    target_link_libraries(client ${Boost_LIBRARIES} -lssl -lcrypto -lpthread)
else()
    target_link_libraries(client ${Boost_LIBRARIES})
endif()
