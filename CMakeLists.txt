cmake_minimum_required(VERSION 3.10)
project(ProjectTemplate)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)

# Force ccache usage
find_program(CCACHE_PROGRAM ccache)
if(CCACHE_PROGRAM)
    set(CMAKE_CXX_COMPILER_LAUNCHER "${CCACHE_PROGRAM}")
    set(CMAKE_C_COMPILER_LAUNCHER "${CCACHE_PROGRAM}")
else()
    message("ccache not found")
endif()

# Add DEBUG options for debug builds
set(CMAKE_CXX_FLAGS_DEBUG "-g -O0")
set(CMAKE_CXX_FLAGS_RELEASE "-O2")

# Find all C++ source files (these get compiled)
file(GLOB SOURCES 
    "src/*.cpp"
    "src/*.cxx" 
    "src/*.cc"
    "src/*.c++"
    "src/*.cp"
    "src/*.c"
)

# Find all C source files if you have any
file(GLOB C_SOURCES "src/*.c")

# Find header files (for IDE support, not compilation)
file(GLOB HEADERS 
    "src/*.hh"
    "src/*.hpp"
    "src/*.hxx"
    "src/*.h++"
    "src/*.hp"
)

# Create executable with all source files
add_executable(app ${SOURCES} ${C_SOURCES} ${HEADERS})
