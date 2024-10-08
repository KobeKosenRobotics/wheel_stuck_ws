cmake_minimum_required(VERSION 3.5)
project(simple_int_subscriber)

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

ament_auto_add_library(simple_int_subscriber SHARED
  src/simple_int_subscriber.cpp
)

rclcpp_components_register_node(simple_int_subscriber
  PLUGIN "simple_int_subscriber::SimpleIntSubscriber"
  EXECUTABLE simple_int_subscriber_node
)

ament_auto_add_library(polling_int_subscriber SHARED
  src/polling_int_subscriber.cpp
)

rclcpp_components_register_node(polling_int_subscriber
  PLUGIN "simple_int_subscriber::PollingIntSubscriber"
  EXECUTABLE polling_int_subscriber_node
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_auto_package(INSTALL_TO_SHARE
  config
  launch
)
