<div align="center">
  <h1>🚀 4-Wheeled AMR: SLAM & Navigation 🛰️</h1>
  <p><b>Autonomous Navigation Stack | ROS 2 Jazzy | Gazebo & RViz2 Simulation</b></p>

  <img src="https://img.shields.io/badge/ROS2-Jazzy-blue?style=for-the-badge&logo=ros" />
  <img src="https://img.shields.io/badge/Ubuntu-24.04-orange?style=for-the-badge&logo=ubuntu" />
  <img src="https://img.shields.io/badge/Python-3.12-yellow?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/C%2B%2B-17-blue?style=for-the-badge&logo=c%2B%2B" />

  <br />
  <hr />
</div>
4-Wheeled AMR: SLAM & Navigation Simulation
Framework: ROS 2 Jazzy | Simulation Tools: Gazebo & RViz2



📌 Project Overview
This project demonstrates an end-to-end autonomous navigation stack for a 4-wheeled mobile robot. By utilizing a custom-designed URDF and integrated ROS 2 packages, the robot is capable of mapping unknown environments and navigating autonomously to a target goal while dynamically avoiding obstacles.

🛠 Technical Implementation & Gazebo Plugins
To bridge the gap between simulation and ROS 2, I utilized specific Gazebo plugins to mimic real-world hardware behavior:

1. Movement & Control
Differential Drive Plugin: Integrated the libgazebo_ros_diff_drive.so plugin to handle wheel kinematics. This allows the robot to subscribe to /cmd_vel topics and broadcast its odometry (/odom) back to the navigation stack.

2. Perception & Sensors
2D LiDAR Plugin: Used the libgazebo_ros_ray_sensor.so plugin to simulate a laser scanner for environment perception. This is the primary data source for the SLAM and Nav2 costmaps.

Camera Plugin: Integrated the libgazebo_ros_camera.so plugin to provide a live feed via the /rover_feed topic, allowing for real-time visual monitoring in RViz2.

3. Coordinate Transforms (TF2)
Implemented a robust tf2 transform tree to ensure accurate spatial synchronization between the laser_frame, camera_link, and the base_link. This ensures the robot "knows" exactly where its sensors are positioned relative to its center.

📂 Key Launch Files
simulation.launch.py: A unified script to spawn the robot, start Gazebo, and initialize the robot_state_publisher.

online_async_launch.py: Handles real-time, asynchronous mapping via slam_toolbox.

navigation_launch.py: Initializes the Nav2 controllers, planners, and recovery behaviors.

🔄 Project workflow
1) Fusion to URDF Conversion of the 3d Model required, in this case 4 wheeled robot.
2) Simulation Layer (launching both rviz and gazebo files)
3) Autonomous Logic Layer (SLAM & Nav2)

🚀 Execution Guide

# 1. Launch the full Simulation (Gazebo + URDF)
ros2 launch samplebot_description simulation.launch.py

# 2. Run SLAM to build the map
ros2 launch bot_slam online_async_launch.py

# 3. Run Navigation 2 
ros2 launch bot_nav navigation_launch.py


🎥 Simulation Demonstrations


1) RVIZ Movement Simulation:


https://github.com/user-attachments/assets/7e196d5e-7499-4b6d-a12e-92f739f98fb7


2) SLAM Operation Simulation in both Gazebo and Rviz:


https://github.com/user-attachments/assets/d071cc3c-60a7-44d7-aec9-270af33471ee


3) Navigation of AMR simulation (It moves toward the position given using 2D goal pose option in Rviz):


https://github.com/user-attachments/assets/5e5ef9b8-9e8e-4ad7-a146-95c84199b23a





