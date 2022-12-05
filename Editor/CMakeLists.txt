project (Editor)

add_executable(Warlock_Editor src/*.cpp) # Add correct sources for executable Application.cpp, TestLayer.cpp and Sandbox2D.cpp might be available
target_link_libraries(Warlock_Editor 
    PRIVATE 
        Warlock
)