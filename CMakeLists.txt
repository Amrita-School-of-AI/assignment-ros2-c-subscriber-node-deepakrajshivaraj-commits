cmake_minimum_required(VERSION 3.8)
project(ros2_subscriber)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# 1. Find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

# 2. Add the executable target
add_executable(subscriber_node src/subscriber_node.cpp)

# 3. Link the dependencies to the target
ament_target_dependencies(subscriber_node 
  rclcpp 
  std_msgs
)

# 4. Install the executable so 'ros2 run' can find it
install(TARGETS
  subscriber_node
  DESTINATION lib/${PROJECT_NAME})

# 5. Export everything
ament_package()
