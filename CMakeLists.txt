# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# set the c++ version
# set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED TRUE)
#set_property(TARGET tgt PROPERTY C_STANDARD 99)
# Set the project name
project (lua-interpreter)

add_compile_options(-g)

include_directories("includes" "core")
file(GLOB SOURCES "./**/*.c")

# Add an executable
add_executable(luac ${SOURCES})
# linking math library libm. the linker presumes all libraries
# to begin with lib so to link libm you link m 
# see https://stackoverflow.com/questions/34625627/how-to-link-to-the-c-math-library-with-cmake
target_link_libraries(luac m)