cmake_minimum_required(VERSION 3.10.0)
project(hello_triangle LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Ruta a tus dependencias
set(DEPS_DIR /home/agustin/deps)

# Ejecutable
add_executable(hello_triangle
    src/main.cpp
    src/glad.c
)

# Headers (include)
target_include_directories(hello_triangle PRIVATE
    ${DEPS_DIR}/include
)

# Librerías
target_link_directories(hello_triangle  PRIVATE
    ${DEPS_DIR}/lib
)

# Linkeo
target_link_libraries(hello_triangle 
    glfw3
    GL
)


add_custom_command(TARGET hello_triangle POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
        "${CMAKE_CURRENT_SOURCE_DIR}/res"
        "$<TARGET_FILE_DIR:hello_triangle>/res"
    COMMENT "Copiando recursos (shaders) al directorio de salida"
)

