cmake_minimum_required(VERSION 4.2)

project(my-2d-game-engine
        VERSION 0.1.0
        LANGUAGES CXX
)

add_executable(game)

target_sources(game
    PRIVATE
        src/main.cpp
)

target_link_libraries(game
    PRIVATE engine
    PRIVATE project_warnings
)

target_compile_features(game PRIVATE cxx_std_23)
