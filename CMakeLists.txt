cmake_minimum_required(VERSION 3.10)
project(cli11_vendor CXX)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

find_package(CLI11 2.1.0 QUIET)

ament_vendor(cli11_vendor
  SATISFIED ${CLI11_FOUND}
  VCS_URL https://github.com/CLIUtils/CLI11
  VCS_VERSION v2.1.2
  CMAKE_ARGS
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  list(APPEND AMENT_LINT_AUTO_EXCLUDE
    ament_cmake_cppcheck
  )
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
