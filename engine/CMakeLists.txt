cmake_minimum_required(VERSION 4.2)

project(my-2d-game-engine
        VERSION 0.1.0
        LANGUAGES CXX
)

add_library(engine STATIC)

target_sources(engine
    PRIVATE
        src/core/Engine.cpp
        # src/renderer/Renderer.cpp
        # src/assets/AssetManager.cpp
        # src/audio/AudioManager.cpp
        # src/ecs/World.cpp
)

target_include_directories(engine
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}/include   # consumers see engine/include/
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src       # internal headers only
)

target_link_libraries(engine
    PRIVATE project_warnings
    # Add third-party libraries here, e.g.:
    # SDL2::SDL2
    # OpenGL::GL
)

target_compile_features(engine PUBLIC cxx_std_23)
