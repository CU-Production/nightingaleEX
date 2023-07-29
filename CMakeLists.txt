cmake_minimum_required(VERSION 3.26)
project(nightingaleEX)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(3rd_party)

add_custom_command(
        OUTPUT "${PROJECT_SOURCE_DIR}/fonts/include/embedded_font_ShareTechMono.inc"
        COMMAND binary_to_compressed_c -base85 ${PROJECT_SOURCE_DIR}/fonts/ShareTechMono-Regular.ttf ShareTechMono > ${PROJECT_SOURCE_DIR}/fonts/include/embedded_font_ShareTechMono.inc
        COMMENT "Embedding font: ShareTechMono-Regular.ttf"
        MAIN_DEPENDENCY "fonts/ShareTechMono-Regular.ttf"
        VERBATIM)

add_custom_command(
        OUTPUT "${PROJECT_SOURCE_DIR}/fonts/include/embedded_font_fontawesome.inc"
        COMMAND binary_to_compressed_c -base85 ${PROJECT_SOURCE_DIR}/fonts/fontawesome-webfont.ttf fontawesome > ${PROJECT_SOURCE_DIR}/fonts/include/embedded_font_fontawesome.inc
        COMMENT "Embedding font: fontawesome-webfont.ttf"
        MAIN_DEPENDENCY "fonts/fontawesome-webfont.ttf"
        VERBATIM)

add_executable(nightingaleEX
        src/main.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
        ${PROJECT_SOURCE_DIR}/fonts/include/embedded_font_ShareTechMono.inc
        ${PROJECT_SOURCE_DIR}/fonts/include/embedded_font_fontawesome.inc
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
