cmake_minimum_required(VERSION 3.5)
project(velodyne_cloud_separator)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
  set(CMAKE_CXX_STANDARD_REQUIRED ON)
  set(CMAKE_CXX_EXTENSIONS OFF)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

ament_auto_add_library(velodyne_cloud_separator SHARED
  src/velodyne_cloud_separator.cpp
)

rclcpp_components_register_node(velodyne_cloud_separator
  PLUGIN "velodyne_cloud_separator::VelodyneCloudSeparator"
  EXECUTABLE velodyne_cloud_separator_node
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_auto_package(INSTALL_TO_SHARE
  config
  launch
)
