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
cd ~/practice/src
git clone https://github.com/RB0609/Practice_thesis.git
```
3. Install the Dependencies
```bash
cd ~/practice
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```
4. Build the workspace
```bash
cd ~/practice
colcon build
source install/setup.bash
```
5. Steps to launch the simulation file in Gazebo Harmonic and Rviz
Gazebo Harmonic Simulation:
```bash
 ros2 launch unitree_go2_sim unitree_go2_launch.py 
```
## Steps to Perform Navigation 
1. Follow these before Performing the navigation
In go2_params.yaml file which is in scripts folder under unitree_go2_sim
```bash
map_server:
  ros__parameters:
    use_sim_time: true
    yaml_filename: "<path_to_file location>/map.yaml" #Here choose your own folder, where you store "map.yaml" file
    #topic_name: "map"
    #frame_id: "map"
```
in Terminal1:(First launch this file)
```bash
ros2 launch nav2_bringup rviz_launch.py 
```
Here careful with file location<br>
map:=<path_to_file_location>/map.yaml<br>
and<br>
params_file:=<path_to_file_location>/go2_params.yaml<br>
below is the example usage
in Terminal2:
```bash
ros2 launch nav2_bringup bringup_launch.py   use_sim_time:=true   map:=/home/rakesh/map.yaml   params_file:=/home/rakesh/practice/src/unitree_go2_ros2/unitree_go2_sim/scripts/go2_params.yaml
```
## Improvements
1. Working on ekf node
   (a) Fine-tuning the parameters for better result
   (b) Focusing on robot's state estimation 
1. Currently focusing on improvement of robot's gait
2. Planning to perform Sim2Real with Unitree go2 Edu
## References
   
For reference I used this github repo, unitree go2 edu simulation in Gazebo and Harmonic.
```bash
https://github.com/khaledgabr77/unitree_go2_ros2
```
For reference, in order to perform navigation of unitree go2 edu robot, I used the below repo as reference,
```bash
https://github.com/Sayantani-Bhattacharya/unitree_go2_nav
```
