cmake_minimum_required (VERSION 3.8)
project (ToyPathTracing)

include_directories(${PROJECT_SOURCE_DIR}/include)
file(COPY ${CMAKE_SOURCE_DIR}/lib/ DESTINATION ${CMAKE_BINARY_DIR})
file(COPY Resources DESTINATION ${CMAKE_BINARY_DIR})
file(GLOB_RECURSE  src_dir "./src/*.c" "./src/*.h" "./src/*.cpp" )

add_executable (${PROJECT_NAME} test3.cpp ${src_dir})


find_library(STATIC_LIB glfw3.lib PATHS ${CMAKE_SOURCE_DIR}/lib)
target_link_libraries(${PROJECT_NAME} PRIVATE ${STATIC_LIB})

find_library(DYNAMIC_LIB assimp-vc140-mt.dll PATHS ${CMAKE_SOURCE_DIR}/lib)
find_library(DYNAMIC_LIB_IMPORT assimp-vc140-mt.lib PATHS ${CMAKE_SOURCE_DIR}/lib)
target_link_libraries(${PROJECT_NAME} PRIVATE ${DYNAMIC_LIB_IMPORT})


SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR})