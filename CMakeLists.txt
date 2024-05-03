cmake_minimum_required(VERSION 3.26)
project(interpreter)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_BUILD_TYPE "Debug")

set(PROJECT_SOURCE_TARGET ${PROJECT_NAME}_source_target)

add_subdirectory(third)
include_directories(${THIRD_INCLUDE_DIR_LIST})

add_subdirectory(src)

add_executable(${PROJECT_NAME} main.cpp)

target_include_directories(${PROJECT_NAME}
    PUBLIC ${PROJECT_SOURCE_DIR}/include
)

target_link_libraries(${PROJECT_NAME} 
    PUBLIC ${PROJECT_SOURCE_TARGET}
    PUBLIC ${THIRD_LIB_LIST}
)
# get_property(dirs TARGET ${PROJECT_NAME} PROPERTY INCLUDE_DIRECTORIES)
# foreach(dir IN LISTS dirs)
#     message(">>> include_dir = " ${dir})
# endforeach()