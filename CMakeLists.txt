cmake_minimum_required(VERSION 3.16.3)

project(nativefiledialog VERSION 0.0.1 LANGUAGES CXX C)
set (CMAKE_CXX_STANDARD 20)

if (CMAKE_CXX_COMPILER_ID MATCHES "GNU")
    if(CMAKE_SYSTEM MATCHES "Linux")
        set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -std=c++20") # ALL WARNINGS
    endif()
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Wall -O3") # ALL WARNINGS
elseif(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} /MP")    # MULTICORE BUILDS
endif()


set(EXEC_FILES ./src/nfd_common.c ./src/nfd_zenity.c)

add_library(nativefiledialog ${EXEC_FILES})
target_include_directories(nativefiledialog PUBLIC ./src/include)