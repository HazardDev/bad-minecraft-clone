cmake_minimum_required (VERSION 2.6)
project (BadMinecraftClone)
SET(PLATFORM_LIBRARIES glfw3)
if (WIN32)
    link_directories(${CMAKE_SOURCE_DIR}/lib)
    SET(PLATFORM_LIBRARIES ${PLATFORM_LIBRARIES} opengl32)
endif()
if (LINUX)
    SET(PLATFORM_LIBRARIES ${PLATFORM_LIBRARIES} X11 GL pthread dl)
endif()
SET(CMAKE_EXE_LINKER_FLAGS  "-static-libgcc -static-libstdc++" )
SET(CMAKE_CXX_FLAGS "-std=c++11")
include_directories("${CMAKE_SOURCE_DIR}/include")
add_executable (BadMinecraftClone src/main.cpp src/Universe.cpp src/Shader.cpp src/Camera.cpp src/Block.cpp src/glad.c src/Chunk.cpp)
target_link_libraries (BadMinecraftClone ${PLATFORM_LIBRARIES})