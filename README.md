# LASER UAV LIO-s

This package aggregates all external Laser Inertial Odometry (LIO) algorithms integrated for use in the system.

## Integrated Algorithms

### FAST-LIO
-   **Description:** FAST-LIO (Fast LiDAR-Inertial Odometry) is a computationally efficient and robust LIO framework. It utilizes a tightly-coupled iterated Error-State Kalman Filter (IESKF) to fuse LiDAR feature points with IMU data. This approach ensures high-accuracy state estimation and mapping capabilities, even in cluttered environments or during aggressive UAV motion.

-   **Reference:**
    W. Xu, Y. Cai, D. He, J. Lin and F. Zhang, "FAST-LIO2: Fast Direct LiDAR-Inertial Odometry," in IEEE Transactions on Robotics, vol. 38, no. 4, pp. 2053-2073, Aug. 2022, doi: 10.1109/TRO.2022.3141876.
