# 检查cmake的最低版本
cmake_minimum_required(VERSION 3.10.0)

# 设置在VS中建立文件夹
SET_PROPERTY( GLOBAL PROPERTY USE_FOLDERS ON )

# 定义工程名称
project(OpengGL_learn)

set(GLFW_INCLUDE_DIR D:/Froler/environment/GLFW334_64/include)
set(GLFW_LIB D:/Froler/environment/GLFW334_64/lib/glfw3.lib)
set(GLAD_INCLUDE_DIR D:/Froler/environment/glad/include)

#添加依赖的头文件
include_directories(
    ${GLFW_INCLUDE_DIR}
	${GLAD_INCLUDE_DIR}
)

#收集文件
file(GLOB SOURCES ${CMAKE_SOURCE_DIR}/*.cpp)
file(GLOB HEADERS ${CMAKE_SOURCE_DIR}/*.h)

#生成可执行程序
add_executable(${PROJECT_NAME}
	${HEADERS}
	${SOURCES}
	${GLAD_INCLUDE_DIR}/../src/glad.c
)

#此处添加依赖库
target_link_libraries(${PROJECT_NAME}
	${GLFW_LIB}
)