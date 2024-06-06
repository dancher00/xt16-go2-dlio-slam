

# Make a docker image and a docker container

```sh
cd docker
docker build -t go2-humble:latest .
```


```sh
git clone https://github.com/TechShare-inc/go2_unitree_ros2.git -b imu_publisher
git clone https://github.com/TechShare-inc/HesaiLidar_General_ROS-ROS2.git
git clone https://github.com/unitreerobotics/unitree_ros2.git
git clone https://github.com/TechShare-inc/direct_lidar_inertial_odometry.git
```

```
$ cd ..
$ bash ../docker/humble.sh
# cd external/
# colcon build --symlink-install
```

unitree_ros2
eth0

