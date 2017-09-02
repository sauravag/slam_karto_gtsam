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

find_package(MKL)
find_package(Eigen REQUIRED)
# find_package(PkgConfig REQUIRED)
find_package(GTSAM REQUIRED)

include_directories(
    include/${PROJECT_NAME}
    ${catkin_INCLUDE_DIRS} 
    ${EIGEN_INCLUDE_DIRS}
    ${GTSAM_INCLUDE_DIRS}
    ${MKL_INCLUDE_DIRS}
)

add_definitions(${EIGEN_DEFINITIONS})

catkin_package()

add_executable(slam_karto_gtsam src/slam_karto_gtsam.cpp src/GTSAMSolver.cpp)

target_link_libraries(slam_karto_gtsam gtsam ${catkin_LIBRARIES} ${MKL_LIBRARIES})

#install(TARGETS slam_karto_gtsam
#  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
#)
