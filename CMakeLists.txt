cmake_minimum_required(VERSION 4.2)
project(xglm C)

set(CMAKE_C_STANDARD 23)

aux_source_directory(src SRC)
add_library(xglm STATIC ${SRC})
target_compile_options(xglm PRIVATE "-msse4" "-mavx2" "-O3")
target_include_directories(xglm PUBLIC src)

if (XGLM_BUILD_DEBUG)
    add_executable(debug test/debug.c)
    target_link_libraries(debug PRIVATE xglm)
endif ()
