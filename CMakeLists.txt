cmake_minimum_required(VERSION 3.5)
project(hitbot_msgs)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)

find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Add hitbot_srv
rosidl_generate_interfaces(${PROJECT_NAME}
"srv/SetGPIO.srv"
"srv/GetGPIOOut.srv"
"srv/GetGPIOIn.srv"
"srv/SetDragTeach.srv"
"srv/JointHome.srv"
"srv/NewMovejXYZ.srv"
"srv/NewMovejAngle.srv"

)

if(BUILD_TESTING)

  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()

endif()

ament_package()
