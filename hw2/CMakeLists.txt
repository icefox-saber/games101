find_package(OpenCV REQUIRED)

add_executable(Rasterizer2 main.cpp rasterizer.hpp rasterizer.cpp global.hpp Triangle.hpp Triangle.cpp)

target_include_directories(Rasterizer2 PRIVATE ${OpenCV_INCLUDE_DIRS})
target_link_libraries(Rasterizer2 PRIVATE ${OpenCV_LIBRARIES})
