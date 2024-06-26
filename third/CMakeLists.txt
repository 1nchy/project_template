cmake_minimum_required(VERSION 3.26)
project(third)

set(THIRD_INCLUDE_LIST "")
set(THIRD_LIB_DIR_LIST "")
set(THIRD_LIB_LIST "")

macro(add_third_libraries lib_name)
    message(STATUS "add third library: " ${lib_name})
    if (NOT EXISTS ${PROJECT_SOURCE_DIR}/${lib_name})
        message(FATAL_ERROR ${lib_name} " not found.")
    endif()
    add_subdirectory(${lib_name})
    list(APPEND THIRD_LIB_DIR_LIST ${PROJECT_SOURCE_DIR}/${lib_name}/lib)
    list(APPEND THIRD_LIB_LIST ${lib_name})
    list(APPEND THIRD_INCLUDE_LIST ${PROJECT_SOURCE_DIR}/${lib_name}/include)
endmacro(add_third_libraries)

macro(add_headonly_third_libraries lib_name)
    message(STATUS "add third library: " ${lib_name})
    if (NOT EXISTS ${PROJECT_SOURCE_DIR}/${lib_name})
        message(FATAL_ERROR ${lib_name} " not found.")
    endif()
    add_subdirectory(${lib_name})
    list(APPEND THIRD_INCLUDE_LIST ${PROJECT_SOURCE_DIR}/${lib_name}/include)
endmacro(add_headonly_third_libraries)

add_third_libraries(third_lib1)  # replace your third lib name
add_third_libraries(third_lib2)  # replace your third lib name
add_headonly_third_libraries(third_lib3)  # replace your third lib name

set(THIRD_INCLUDE_LIST ${THIRD_INCLUDE_LIST} PARENT_SCOPE)
set(THIRD_LIB_DIR_LIST ${THIRD_LIB_DIR_LIST} PARENT_SCOPE)
set(THIRD_LIB_LIST ${THIRD_LIB_LIST} PARENT_SCOPE)
