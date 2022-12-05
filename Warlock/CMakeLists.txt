project( Warlock )

# Add Global variables

# Add external dependencies

# Add Sources (add subfolders of Warlock and Platform too if they are implemented. Also add dependencies without CMake Suport here for now until dependency handling is implemented)
file(GLOB
    SOURCES CONFIGURE_DEPENDS
        "src/Warlock/*.cpp"
        "src/Platform/*.cpp"
)

# Create Library
add_library(Warlock
    STATIC
        ${SOURCES}
)

## Link external libraries (only those with cmake support
target_link_libraries(Warlock
    PUBLIC
)

## Add pre-compiled headers
target_precompile_headers(Warlock
    PUBLIC
        src/WarlockPCH.hpp
)

## Add include directories
target_include_directories(Warlock
    PUBLIC
        src
        src/Warlock
        src/Platform
    PRIVATE
        vendor/*
)