cmake_minimum_required(VERSION 3.10)

project(lri_extractor)

set (CMAKE_CXX_STANDARD 20)

if(MSVC)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

include_directories(SYSTEM src/ext)

add_executable(lri_extractor
    src/main.cpp
    src/image.cpp
    src/debayer.cpp
    src/picoproto.cpp
    src/utils.cpp
    src/stb_image.cpp
)

if(MSVC)
  target_compile_options(lri_extractor PRIVATE /W4 /WX)
else()
  target_compile_options(lri_extractor PRIVATE -Wall -Wextra -Wpedantic -Werror -Wconversion)
endif()