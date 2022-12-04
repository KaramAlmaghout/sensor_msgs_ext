cmake_minimum_required(VERSION 3.8)
project(sensor_msgs_ext)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)
rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/AxisState.msg"
  "msg/Proximity.msg"
  "msg/AnalogVoltage.msg"
  "msg/TimeReference.msg"
  "msg/GnssFix.msg"
  "msg/GnssPosition.msg"
  "msg/GnssTrack.msg"
  "msg/Accelerometer.msg"
  "msg/Gyroscope.msg"
  "msg/Magnetometer.msg"
  "msg/Temperature.msg"
  "msg/Covariance.msg"

  "srv/CalibrateGyroscope.srv"
  "srv/SetAxisHome.srv"
  "srv/GetProximityConfiguration.srv"
  DEPENDENCIES builtin_interfaces
 )

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
