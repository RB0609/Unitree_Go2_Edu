# Autonomous indoor navigation for a quadruped robot using 3D LiDAR and RGB-D sensing

<img width="1836" height="1009" alt="image" src="https://github.com/user-attachments/assets/07fe9044-4535-41b2-a32a-765d9663602b" />

## Watch this below video for Navigation

https://github.com/user-attachments/assets/4b23e7d9-05f6-4085-8a9f-3eeae7db333f

## ROS 2 System Architecture
<img width="1401" height="709" alt="go2" src="https://github.com/user-attachments/assets/64bf0008-3680-4abb-be2a-3bd3273a5d16" />

## Features
- Simulation in an indoor environment in **Gazebo Harmonic**
- Navigation (using **Nav2 Stack**) from Point A to Point B, using **"Nav2goal"**.

## Steps I have followed to achieve Navigation
1. Took a pre-built indoor- environment from **Fuel model** available for Gazebo.
2. Launched the robot and Indoor environment in **Gazebo Harmonic**.
3. Made some necessary changes in the world for **simulation** ready.
4. Built the map using **slam toolbox**.
5. Launched Nav2_bringup with:<br>
   (a) **Map-server**: loads my saved map.<br>
   (b) **amcl** for **localization** on that map.<br>
   (c) planner_server, controller_server, bt_navigator, etc. for **navigation**<br>
   (d) **rviz2** for visualization and setting goals using **"Nav2goal"**.<br>
   (e) **Local & global costmaps** configured in params_file.<br>
   (f) Fine-tune few parameters in params_file in order to get good results.<br>

## Requirements
- Ubuntu 24.04
- ROS 2 Jazzy Jalisco
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
https://github.com/RB0609/Unitree_Go2_Edu.git
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
For below code, careful with file location<br>
map:=<path_to_file_location>/map.yaml<br>
params_file:=<path_to_file_location>/go2_params.yaml<br>
below is the example usage<br>
in Terminal2:
```bash
ros2 launch nav2_bringup bringup_launch.py   use_sim_time:=true   map:=/home/rakesh/map.yaml   params_file:=/home/rakesh/practice/src/unitree_go2_ros2/unitree_go2_sim/scripts/go2_params.yaml
```
## Further work
1. Working on **ekf node**<br>
   (a) Fine-tuning the parameters for better result<br>
   (b) Focusing on robot's state estimation <br>
1. Currently focusing on improvement of robot's gait<br>
2. Planning to perform **Sim2Real** with **Unitree go2 Edu**
## References
   
For reference I used this github repo, unitree go2 edu simulation in Gazebo and Harmonic.
```bash
https://github.com/khaledgabr77/unitree_go2_ros2
```
For reference, in order to perform navigation of unitree go2 edu robot, I used the below repo as reference,
```bash
https://github.com/Sayantani-Bhattacharya/unitree_go2_nav
```
Here's the link for the Gazebo model
```bash
https://app.gazebosim.org/OpenRobotics/fuel/models/Depot
```
Nav2 stack doc
```bash
https://docs.nav2.org/index.html
```
