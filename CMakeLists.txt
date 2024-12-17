# Minimum viable CMakeLists.txt file for compiling the serialport library using cmake.

cmake_minimum_required(VERSION 3.27)

project(WjwwoodSerial)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

if(WIN32)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)    
endif()

file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_LIST_DIR}/src/*.cc)
file(GLOB_RECURSE HEADERS ${CMAKE_CURRENT_LIST_DIR}/include/*.h)

# Add the library
set(TARGET_LIB WjwwoodSerial)
add_library(${TARGET_LIB} SHARED 
    ${SOURCES}
    ${HEADERS}
)
if(WIN32)
    target_link_libraries(${TARGET_LIB} PRIVATE Setupapi)
endif()

set_target_properties(${TARGET_LIB} PROPERTIES DEBUG_POSTFIX "d")
target_compile_features(${TARGET_LIB} PRIVATE cxx_std_17)

# Include directories
target_include_directories(${TARGET_LIB} PRIVATE 
    ${CMAKE_CURRENT_LIST_DIR}/include
)
