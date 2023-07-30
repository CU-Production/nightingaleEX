cmake_minimum_required(VERSION 3.26)
project(nightingaleEX)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(3rd_party)

add_executable(nightingaleEX-glfw-ogl33
        src/main_glfw_ogl33.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
        src/backends/imgui_impl_glfw.cpp
        src/backends/imgui_impl_opengl3.cpp
)
target_include_directories(nightingaleEX-glfw-ogl33 PRIVATE
        fonts/include
)
target_link_libraries(nightingaleEX-glfw-ogl33 PRIVATE
        glfw
        imgui
        miniaudio
        nfd
        pffft
)
add_custom_command(
        TARGET nightingaleEX-glfw-ogl33 POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fonts ${CMAKE_CURRENT_BINARY_DIR}/fonts
)

add_executable(nightingaleEX-win32-dx11
        src/main_win32_dx11.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
        src/backends/imgui_impl_win32.cpp
        src/backends/imgui_impl_dx11.cpp
)
target_include_directories(nightingaleEX-win32-dx11 PRIVATE
        fonts/include
)
target_link_libraries(nightingaleEX-win32-dx11 PRIVATE
        imgui
        miniaudio
        nfd
        pffft
)
add_custom_command(
        TARGET nightingaleEX-win32-dx11 POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fonts ${CMAKE_CURRENT_BINARY_DIR}/fonts
)

add_executable(nightingaleEX-win32-dx12
        src/main_win32_dx12.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
        src/backends/imgui_impl_win32.cpp
        src/backends/imgui_impl_dx12.cpp
)
target_include_directories(nightingaleEX-win32-dx12 PRIVATE
        fonts/include
)
target_link_libraries(nightingaleEX-win32-dx12 PRIVATE
        imgui
        miniaudio
        nfd
        pffft
)
add_custom_command(
        TARGET nightingaleEX-win32-dx12 POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fonts ${CMAKE_CURRENT_BINARY_DIR}/fonts
)

find_package(Vulkan REQUIRED)
add_executable(nightingaleEX-glfw-vk
        src/main_glfw_vk.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
        src/backends/imgui_impl_glfw.cpp
        src/backends/imgui_impl_vulkan.cpp
)
target_include_directories(nightingaleEX-glfw-vk PRIVATE
        fonts/include
)
target_link_libraries(nightingaleEX-glfw-vk PRIVATE
        glfw
        imgui
        miniaudio
        nfd
        pffft
        Vulkan::Vulkan
)
add_custom_command(
        TARGET nightingaleEX-glfw-vk POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fonts ${CMAKE_CURRENT_BINARY_DIR}/fonts
)

add_executable(nightingaleEX-win32-ogl33
        src/main_win32_ogl33.cpp
        src/app.cpp
        src/audio.cpp
        src/widgets.cpp
        src/backends/imgui_impl_win32.cpp
        src/backends/imgui_impl_opengl3.cpp
)
target_include_directories(nightingaleEX-win32-ogl33 PRIVATE
        fonts/include
)
target_link_libraries(nightingaleEX-win32-ogl33 PRIVATE
        imgui
        miniaudio
        nfd
        pffft
)
add_custom_command(
        TARGET nightingaleEX-win32-ogl33 POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory
        ARGS ${CMAKE_CURRENT_SOURCE_DIR}/fonts ${CMAKE_CURRENT_BINARY_DIR}/fonts
)
