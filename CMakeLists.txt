# cmake_minimum_required(VERSION <specify CMake version here>)
cmake_minimum_required(VERSION 3.14)
project(CJsonObject)

set(CMAKE_CXX_STANDARD 11)

#include the dirctory
set(INC_DIR
       include
    )
include_directories(${INC_DIR})

#add the source code
set(SRC
        src/cJSON.c
        src/CJsonObject.cpp
        )
#generate the dynamic library
set(DYNAMIC_LIB    cjsonobject_dynamic)
add_library(${DYNAMIC_LIB}  SHARED ${SRC})

#generate the static library
set(STATIC_LIB    cjsonobject_static)
add_library(${STATIC_LIB}  STATIC ${SRC})

#generate the test execute file
set(EXE_NAME    cjsonobject_test)
add_executable(${EXE_NAME}      main.cpp)
#link to the library
target_link_libraries(${EXE_NAME}   ${DYNAMIC_LIB})