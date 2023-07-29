cmake_minimum_required(VERSION 3.26)
project(nightingaleEX)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(3rd_party)

add_executable(nightingaleEX
        src/main.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
)
target_include_directories(nightingaleEX PRIVATE
        fonts/include
)
target_link_libraries(nightingaleEX PRIVATE
        glfw
        imgui
        miniaudio
        sokol
        nfd
        pffft
)
add_custom_command(
        TARGET nightingaleEX POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fonts ${CMAKE_CURRENT_BINARY_DIR}/fonts
)
