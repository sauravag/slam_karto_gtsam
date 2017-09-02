# slam_karto_gtsam
Pose-graph SLAM with Open Karto as Front-end and GTSAM as Backend

# Notes

The optimization routine used is Levenberg-Marquadt provided by g2o, you can easily change it to something else (Powell's dog leg etc.). This package is currently tested with Ubuntu 16.04 LTS + ROS Kinetic

# How-To Use

Use the given launch files. The build_map_w_params launch files uses a given param file, which you can edit to change the behavior of open_karto. Make sure to use the right scan topic. Also, the package will expect an odometry tf to be published to between odom frame and base_link (or base_footprint).

# Dependencies

* Download and install Intel MKL from  https://software.intel.com/en-us/mkl

* Download and install GTSAM 4.x, instructions are in GTSAM readme. $ git clone https://bitbucket.org/gtborg/gtsam.git

* Download and put open karto in your catkin_ws/src from https://github.com/ros-perception/open_karto

# Support

Head on over to my blog post http://sauravag.com/2017/07/an-practical-introduction-to-pose-graph-slam/ where you can ask questions and I will try to respond in a timely manner.