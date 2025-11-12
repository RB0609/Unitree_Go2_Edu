# Autonomous indoor navigation for a quadruped robot using 3D LiDAR and RGB-D sensing

<img width="1836" height="1009" alt="image" src="https://github.com/user-attachments/assets/07fe9044-4535-41b2-a32a-765d9663602b" />


## Features
- Robot simulation in a indoor environment in Gazebo Harmonic
- Navigation (using Nav2 Stack) from Point A to Point B, using "Nav2goal" feature from Nav2
  
## Requirements
- Ubuntu 24.04
- ROS 2 Jazzy
- Gazebo Sim Harmonic

## Installation
1. Install ROS2 Dependencies
```bash
sudo apt update
sudo apt install ros-jazzy-gazebo-ros2-control
sudo apt install ros-jazzy-xacro
sudo apt install ros-jazzy-robot-localization
sudo apt install ros-jazzy-ros2-controllers
sudo apt install ros-jazzy-ros2-control
sudo apt install ros-jazzy-velodyne
sudo apt install ros-jazzy-velodyne-description
```
2. Clone the Go2 Simulation package
```bash
cd ~/folder_ws/src
git clone https://github.com/<you>/<repo>.git
```
3. Install the Dependencies
```bash
cd ~/folder_ws
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```
4. Build the workspace
```bash
cd ~/folder_ws
colcon build
source install/setup.bash
```
5. References
   
For reference I used this github repo, unitree go2 edu simulation in Gazebo and Harmonic.
```bash
https://github.com/khaledgabr77/unitree_go2_ros2
```
For reference, in order to perform navigation of unitree go2 edu robot, I used the below repo as reference,
```bash
https://github.com/Sayantani-Bhattacharya/unitree_go2_nav
```
