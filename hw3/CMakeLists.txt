find_package(OpenCV REQUIRED)

set(CMAKE_CXX_STANDARD 17)

# 自动复制 models 目录到 build/hw3/
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/models DESTINATION ${CMAKE_BINARY_DIR})

add_executable(Rasterizer3 main.cpp rasterizer.hpp rasterizer.cpp global.hpp Triangle.hpp Triangle.cpp Texture.hpp Texture.cpp Shader.hpp OBJ_Loader.h)
target_link_libraries(Rasterizer3 ${OpenCV_LIBRARIES})
target_include_directories(Rasterizer3 PRIVATE ${OpenCV_INCLUDE_DIRS})
enable_testing()
enable_testing()
add_test(NAME nomal_test
         COMMAND ./Rasterizer3 normal.png normal
         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})

add_test(NAME phong_test
         COMMAND ./Rasterizer3 phong.png phong
         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})
add_test(NAME texture_test
         COMMAND ./Rasterizer3 texture.png texture
         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})
add_test(NAME bump_test
         COMMAND ./Rasterizer3 bump.png  bump
         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})

add_test(NAME displacement_test
         COMMAND ./Rasterizer3 displacement.png  displacement
         WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})
#target_compile_options(Rasterizer PUBLIC -Wall -Wextra -pedantic)