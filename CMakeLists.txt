cmake_minimum_required(VERSION 3.8)

set(CMAKE_CXX_STANDARD 20)

project("InkBall")

# add_subdirectory(${PROJECT_SOURCE_DIR}/include/mingw)
include_directories(${PROJECT_SOURCE_DIR}/include)
link_directories(${PROJECT_SOURCE_DIR}/lib/x64)

add_executable(InkBall "main.cpp"  "Game.cpp" "Game.h")

target_link_libraries(InkBall SDL2main SDL2 SDL2_image SDL2_ttf)

# game assets and runtimes
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/assets DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/game_levels DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
file(GLOB RUNTIME_DLLS ${CMAKE_CURRENT_SOURCE_DIR}/lib/x64/*.dll)
file(COPY ${RUNTIME_DLLS} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
