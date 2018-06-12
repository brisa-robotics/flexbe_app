cmake_minimum_required(VERSION 2.8.3)
project(flexbe_app)

find_package(catkin REQUIRED)

catkin_package(
    INCLUDE_DIRS src
    LIBRARIES ${PROJECT_NAME})

execute_process(COMMAND npm --prefix ${PROJECT_SOURCE_DIR} install)

install(PROGRAMS bin/run_app
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

install(FILES package.json
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

install(DIRECTORY
  node_modules
  launch
  src
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  USE_SOURCE_PERMISSIONS)
