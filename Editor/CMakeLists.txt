project (Editor)

# Defining Executable
add_executable(Warlock_Editor src/EditorApp.cpp) # Add correct sources for executable Application.cpp, TestLayer.cpp and Sandbox2D.cpp might be available

# Link Engine Library to the Editor executable
target_link_libraries(Warlock_Editor 
    PRIVATE 
        Warlock
)