cmake_minimum_required(VERSION 3.5)
project(ros2_bag_to_image)


## Default to C99
#if(NOT CMAKE_C_STANDARD)
#  set(CMAKE_C_STANDARD 99)
#endif()

## Default to C++14
#if(NOT CMAKE_CXX_STANDARD)
#  set(CMAKE_CXX_STANDARD 14)
#endif()


set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

find_package(OpenCV REQUIRED)
find_package(Boost REQUIRED)
find_package(rosbag2 REQUIRED)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

# bag_to_image
ament_auto_add_library(bag_to_image SHARED
        src/bag_to_image.cpp
        )

target_link_libraries(bag_to_image ${PCL_LIBRARIES}
        )

target_include_directories(bag_to_image
        SYSTEM PUBLIC
        ${OpenCV_INCLUDE_DIRS}
        )

rclcpp_components_register_node(bag_to_image
        PLUGIN "BagToImage"
        EXECUTABLE bag_to_image_node
        )

ament_auto_package(INSTALL_TO_SHARE
        launch
)

