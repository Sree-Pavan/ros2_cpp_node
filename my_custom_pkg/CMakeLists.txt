cmake_minimum_required(VERSION 3.8)
project(my_custom_pkg)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)

# Include cpp "include" directory
include_directories(include)

#Create cpp executables

add_executable(cpp_exe src/cpp_node.cpp)
ament_target_dependencies(cpp_exe rclcpp)

#Install cpp executables

install(TARGETS
  cpp_exe
  DESTINATION lib/${PROJECT_NAME}
)


ament_package()
