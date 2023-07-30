# GLFW
set(BUILD_SHARED_LIBS OFF CACHE INTERNAL "shared")
set(GLFW_BUILD_EXAMPLES OFF CACHE INTERNAL "glfw examples")
set(GLFW_BUILD_TESTS OFF CACHE INTERNAL "glfw tests")
set(GLFW_BUILD_DOCS OFF CACHE INTERNAL "glfw docs")
set(GLFW_INSTALL OFF CACHE INTERNAL "glfw install")
set(GLFW_VULKAN_STATIC OFF CACHE INTERNAL "glfw vulkan")
add_subdirectory(glfw)

# imgui
add_library(imgui STATIC
        imgui/imgui.cpp
        imgui/imgui_demo.cpp
        imgui/imgui_draw.cpp
        imgui/imgui_tables.cpp
        imgui/imgui_widgets.cpp
)
target_include_directories(imgui PUBLIC
        imgui
)

# miniaudio
add_library(miniaudio INTERFACE)
target_include_directories(miniaudio INTERFACE miniaudio)

# nativefiledialog-extended
add_subdirectory(nativefiledialog-extended)

# pffft
add_library(pffft INTERFACE)
target_include_directories(pffft INTERFACE pffft)
