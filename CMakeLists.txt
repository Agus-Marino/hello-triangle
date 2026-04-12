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
