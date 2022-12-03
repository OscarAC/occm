cmake_minimum_required(VERSION 3.22)
project(occm)


#[==[==========================================================
                        CMake Config
==========================================================#]==]
include(CMakePackageConfigHelpers)

set (CMAKE_MODULE_PATH "${CMAKE_MODULE_PATH};${CMAKE_CURRENT_SOURCE_DIR}/cmake")

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS ON)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)



#[==[==========================================================
                        Doxygen
==========================================================#]==]
find_package(Doxygen)
if(Doxygen_FOUND)
    add_subdirectory(docs)
else()
    message(STATUS "Doxygen not found, skipping documentation generation")
endif()


#[==[==========================================================
                        OCCommon Lib
==========================================================#]==]
add_library(occm INTERFACE)
target_include_directories(occm INTERFACE include)
target_compile_options(occm INTERFACE -Wall)
