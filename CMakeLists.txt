cmake_minimum_required(VERSION 3.13)
cmake_policy(SET CMP0167 NEW)

set(CMAKE_OSX_ARCHITECTURES "arm64")

set(CMAKE_TOOLCHAIN_FILE "$ENV{HOME}/vcpkg/scripts/buildsystems/vcpkg.cmake")
message(STATUS "vcpkg toolchain: ${CMAKE_TOOLCHAIN_FILE}")

project(simple_example)
set(CMAKE_CXX_STANDARD 20)

find_package(Boost REQUIRED)
if (Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
    link_directories(${Boost_LIBRARY_DIRS})
endif ()

set(SOURCE_FILES main.cpp)

add_executable(simple_example ${SOURCE_FILES})

target_link_libraries(simple_example PUBLIC ${Boost_LIBRARIES})
