cmake_minimum_required(VERSION 3.25)
project(shadow_mapping)

set(CMAKE_CXX_STANDARD 17)

add_executable(shadow_mapping main.cpp)

# 暂存环境变量
set(GLFW_HOME "/Users/yangkai/OpenGL/glfw")
set(GLAD_HOME "/Users/yangkai/OpenGL/glad")
set(GLM_HOME "/Users/yangkai/OpenGL/glm")
set(ASSIMP_HOME "/Users/yangkai/OpenGL/assimp")
set(STB_HOME "/Users/yangkai/OpenGL/stb")

# 设置头文件目录
include_directories("${GLFW_HOME}/include")
include_directories("${GLAD_HOME}/include")
include_directories("${GLM_HOME}")
include_directories("${ASSIMP_HOME}/include")
include_directories("${STB_HOME}")

# 添加 GLFW3 预编译库
add_library(glfw SHARED IMPORTED)
SET_TARGET_PROPERTIES(glfw PROPERTIES IMPORTED_LOCATION "${GLFW_HOME}/lib-x86_64/libglfw.3.dylib")

# 编译 GLAD 库
add_library(glad SHARED "${GLAD_HOME}/src/glad.c")

# 创建可执行文件
#add_executable(FirstOpenGL main.cpp)

# 链接 GLFW GLAD OpenGL
target_link_libraries(shadow_mapping glfw glad "-framework OpenGL")

