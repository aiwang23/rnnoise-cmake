cmake_minimum_required(VERSION 3.30)

project(rnnoise)

set(CMAKE_C_STANDARD 11)

file(GLOB RNNOISE_SOURCES
        "rnnoise/src/*.c"
        "rnnoise/src/*.h"
        "data/*.c"
        "data/*.h"
)

add_library(rnnoise STATIC ${RNNOISE_SOURCES})

target_include_directories(rnnoise PUBLIC "rnnoise/src")
target_include_directories(rnnoise PUBLIC "rnnoise/include")
target_include_directories(rnnoise PUBLIC "rnnoise")
target_include_directories(rnnoise PUBLIC "data")
if (MSVC)
    target_include_directories(rnnoise PUBLIC "msvc_include")
    target_compile_definitions(rnnoise PRIVATE _USE_MATH_DEFINES)
endif ()