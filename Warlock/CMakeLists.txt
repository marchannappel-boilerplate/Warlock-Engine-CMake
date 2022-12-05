project( Warlock )

# Add Global variables

# Add external dependencies

# Add Sources

# Create Library
add_library(Warlock
    STATIC
        ${SOURCES}
)

## Link external libraries
target_link_libraries(Warlock
    PUBLIC
)

## Add pre-compiled headers
target_precompile_headers(Warlock
    PUBLIC
        WarlockPCH.h
)

## Add include directories
target_include_directories(Warlock
    PUBLIC
        src
    PRIVATE
        vendor/*
)