project( FrostForge )

set(CPM_DOWNLOAD_VERSION 0.27.2) 
set(CPM_DOWNLOAD_LOCATION "${CMAKE_BINARY_DIR}/cmake/CPM_${CPM_DOWNLOAD_VERSION}.cmake")

if(NOT (EXISTS ${CPM_DOWNLOAD_LOCATION}))
    message(STATUS "Downloading CPM.cmake")
    file(DOWNLOAD https://github.com/TheLartians/CPM.cmake/releases/download/v${CPM_DOWNLOAD_VERSION}/CPM.cmake ${CPM_DOWNLOAD_LOCATION})
endif()

include(${CPM_DOWNLOAD_LOCATION})

# Add Global variables

# Add CPMPackages for editor here with CPMAddPackage(NAME <PackageName> VERSION <Version> GITHUB_REPOSITORY <GitRepository> GIT_TAG <GitTag>)
# Example: CPMAddPackage(NAME FrostForge VERSION 0.0.1 GITHUB_REPOSITORY TheLartians/FrostForge)

# Add Sources
file(GLOB SOURCES CONFIGURE_DEPENDS
    src/*.cpp
)

# Create Library
add_library(FrostForge
    STATIC
        ${SOURCES}
)

## Link external libraries
target_link_libraries(FrostForge
    PUBLIC
)

## Add pre-compiled headers
target_precompile_headers(FrostForge
    PUBLIC
        FrostForgePCH.h
)

## Add include directories
target_include_directories(FrostForge
    PUBLIC
        src
        src/Warlock
        src/Platform
    PRIVATE
        vendor/*
)