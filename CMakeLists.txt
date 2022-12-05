cmake_minimum_required(VERSION 3.5)
project(Warlock_Engine VERSION 0.0.1 LANGUAGES CXX)

## 64 Bit Check
if(NOT CMAKE_SIZEOF_VOID_P MATCHES 8)
    message(FATAL_ERROR "Warlock Engine only supports 64-bit builds.")
endif()

## OS Check for builds on different 
if("${CMAKE_SYSTEM_NAME}" STREQUAL "Windows")
	set(OS_WINDOWS 1)
elseif("${CMAKE_SYSTEM_NAME}" STREQUAL "Darwin")
	set(OS_MACOSX 1)
elseif("${CMAKE_SYSTEM_NAME}" STREQUAL "Linux")
    set(OS_Linux 1)
endif()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

## Engine definition
file(GLOB ENGINESOURCES "Engine/src/*.cpp" "Engine/src/*.h")
add_library(Warlock SHARED ${ENGINESOURCES})

## Editor definition
file(GLOB EDITORSOURCES "Editor/src/*.cpp" "Editor/src/*.h")
add_executable(Warlock-Editor ${EDITORSOURCES})


target_link_libraries(Warlock-Editor
    Warlock
)
