cmake_minimum_required(VERSION 3.5)
project(wheel_stuck_launcher)

find_package(ament_cmake_auto REQUIRED)
ament_auto_find_build_dependencies()

ament_auto_package(INSTALL_TO_SHARE
  launch
  config
)
