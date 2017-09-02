cmake_minimum_required(VERSION 2.8.3)
project(slam_karto_gtsam)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
    cmake_modules
    message_filters
    nav_msgs
    open_karto
    rosconsole
    roscpp
    sensor_msgs
    geometry_msgs
    tf
    visualization_msgs
)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${PROJECT_SOURCE_DIR}/CMakeModules/")

find_package(MKL REQUIRED)
find_package(PkgConfig REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(GTSAM REQUIRED)

include_directories(
    include/${PROJECT_NAME}
    ${catkin_INCLUDE_DIRS} 
    ${EIGEN_INCLUDE_DIRS}
    ${MKL_INCLUDE_DIR}
    ${GTSAM_INCLUDE_DIRS}
)

catkin_package(
 INCLUDE_DIRS include
 CATKIN_DEPENDS roscpp message_filters nav_msgs open_karto rosconsole roscpp sensor_msgs geometry_msgs tf visualization_msgs 
 DEPENDS Eigen3
)

add_executable(slam_karto_gtsam src/slam_karto_gtsam.cpp src/GTSAMSolver.cpp)

target_link_libraries(slam_karto_gtsam gtsam ${catkin_LIBRARIES} ${MKL_LIBRARIES})

#install(TARGETS slam_karto_gtsam
#  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
#)
