cmake_minimum_required(VERSION 4.2)

project(my-2d-game-engine
    VERSION 0.1.0
    LANGUAGES CXX
)

# ── C++23 globally ────────────────────────────────────────────────────────────
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)   # use -std=c++23, not -std=gnu++23

# ── Build type default ────────────────────────────────────────────────────────
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
    set(CMAKE_BUILD_TYPE Debug CACHE STRING "Build type" FORCE)
endif()

# ── Compiler warnings ─────────────────────────────────────────────────────────
add_library(project_warnings INTERFACE)
if(MSVC)
    target_compile_options(project_warnings INTERFACE /W4 /WX /permissive-)
else()
    target_compile_options(project_warnings INTERFACE
            -Wall -Wextra -Wpedantic -Werror
    )
endif()

# ── Sub-projects ──────────────────────────────────────────────────────────────
add_subdirectory(engine)
add_subdirectory(game)