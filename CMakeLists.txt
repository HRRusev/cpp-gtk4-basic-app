cmake_minimum_required(VERSION 3.19)
project(GTK4 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Use the package PkgConfig to detect GTK+ headers/library files
FIND_PACKAGE(PkgConfig REQUIRED)
pkg_check_modules(GTKMM REQUIRED gtkmm-4.0)


# Setup CMake to use GTK+, tell the compiler where to look for headers
# and to the linker where to look for libraries
include_directories(${GTKMM_INCLUDE_DIRS})
link_directories(${GTKMM_LIBRARY_DIRS})
add_definitions(${GTKMM_CFLAGS_OTHER})


# Add other flags to the compiler
ADD_DEFINITIONS(${GTK4_CFLAGS_OTHER})

include_directories(include)

# Specify the source files
add_executable(${PROJECT_NAME}
    src/main.cpp
    src/MyWindow.cpp

    include/MyWindow.h
)

target_link_libraries(${PROJECT_NAME} ${GTKMM_LIBRARIES})



