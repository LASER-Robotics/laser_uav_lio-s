# LASER UAV LIO-s

`laser_uav_lio-s` collects the LiDAR-inertial odometry integration used by the LASER UAV System (LUS). FAST-LIO combines LiDAR scans and IMU measurements to estimate motion and build a local map.

The collection fetches `laser_fast_lio_core`, which contains the LUS launch files and sensor profiles, together with the FAST-LIO implementation. Odometry from this integration feeds `estimation_manager`; registered point clouds can also feed the mapping and planning stack.

## Install and build

From this repository:

```bash
gitman install
```

Gitman stores the integration in `.gitman/` and links it at `ros_packages/laser_fast_lio`. The integration has its own dependency manifest for FAST-LIO. Make those ROS packages available in the workspace and install their declared dependencies before building:

```bash
colcon build --packages-up-to laser_fast_lio_core
source install/setup.bash
```

## Run and configure

Use the integration launch with your point-cloud and IMU topics:

```bash
export UAV_NAME=uav1
ros2 launch laser_fast_lio_core fast_lio.launch.py topic_pcl:=/uav1/livox/lidar topic_imu:=/uav1/livox/imu
```

`fast_lio_config_file_path` selects the sensor YAML. The profiles configure LiDAR preprocessing, IMU noise, LiDAR-to-IMU extrinsics, map resolution and output publication. Use a profile calibrated for your sensors and mounting, and match its frame names to the UAV namespace.

This collection has no node or runtime parameters of its own. See the [integration README](ros_packages/laser_fast_lio/README.md) for launch arguments, parameters and ROS inputs and outputs.

## Reference

W. Xu, Y. Cai, D. He, J. Lin and F. Zhang, "FAST-LIO2: Fast Direct LiDAR-Inertial Odometry," IEEE Transactions on Robotics, 38(4), pp. 2053-2073, 2022. DOI: 10.1109/TRO.2022.3141876.
