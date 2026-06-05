# Robot Modeling and Simulation

A ROS 2 Jazzy project focused on robot modeling, visualization, and simulation using URDF Xacro, TF2, RViz2, and Gazebo Sim.

This project demonstrates the workflow of designing a custom mobile robot, defining its structure using URDF Xacro, publishing transform frames using TF2, visualizing the robot in RViz, and spawning it into a Gazebo simulation environment.

## 🚀 Features

* Custom robot modeling using URDF Xacro
* Gazebo Sim integration for physics simulation
* TF2 transform broadcasting and visualization
* RViz2 robot model visualization
* Custom STL meshes for robot links
* Robot State Publisher integration
* ROS 2 parameter handling (C++ and Python)

## 📁 Project Structure

```
robot_ws/
├── images/                      # Gazebo + RViz screenshots for documentation
│
├── src/
│   ├── robot_cpp/               # C++ nodes for control / parameters
│   │   ├── include/
│   │   ├── src/
│   │   │   └── simple_parameter.cpp
│   │   ├── CMakeLists.txt
│   │   └── package.xml
│   │
│   ├── robot_description/       # Robot model, URDF, meshes, launch files
│   │   ├── launch/
│   │   │   ├── display.launch.py
│   │   │   └── gazebo.launch.py
│   │   ├── meshes/
│   │   │   ├── base_link.STL
│   │   │   ├── caster_front_link.STL
│   │   │   ├── caster_rear_link.STL
│   │   │   ├── imu_link.STL
│   │   │   ├── wheel_left_link.STL
│   │   │   └── wheel_right_link.STL
│   │   ├── rviz/
│   │   │   └── display.rviz
│   │   ├── urdf/
│   │   │   ├── robot.urdf.xacro
│   │   │   └── robot_gazebo.xacro
│   │   ├── CMakeLists.txt
│   │   └── package.xml
│   │
│   ├── robot_py/                # Python ROS 2 utilities
│   │   ├── resource/
│   │   ├── robot_py/
│   │   │   ├── __init__.py
│   │   │   └── simple_parameters.py
│   │   ├── test/
│   │   ├── setup.py
│   │   ├── setup.cfg
│   │   └── package.xml
│
├── .gitignore                   # Ignore build, install, log, vscode, pycache

```

## 🤖 Robot Overview

* Base Link – Main robot body and reference frame
* Left Wheel Link – Drive wheel
* Right Wheel Link – Drive wheel
* Front Caster Link – Passive support wheel
* Rear Caster Link – Passive support wheel
* IMU Link – Inertial Measurement Unit frame

Robot geometry is defined using STL meshes and assembled using URDF Xacro.

## 🛠️ Technologies Used

* ROS 2 Jazzy
* Gazebo Sim
* URDF Xacro
* TF2
* RViz2
* C++
* Python
* Colcon Build System

## 📋 Prerequisites

* Ubuntu 24.04 LTS
* ROS 2 Jazzy
* Gazebo Sim

Install dependencies:

```bash
sudo apt update
sudo apt install ros-jazzy-desktop \
  ros-jazzy-ros-gz \
  ros-jazzy-robot-state-publisher \
  ros-jazzy-joint-state-publisher-gui
```

Install workspace dependencies:

```bash
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```

## 🔨 Build the Workspace

```bash
cd ~/robot_ws
colcon build --symlink-install
source install/setup.bash
```

## ▶️ Run Gazebo Simulation

```bash
ros2 launch robot_description gazebo.launch.py
```

This will:

* Load the robot model
* Start Robot State Publisher
* Publish TF frames
* Launch Gazebo Sim
* Spawn the robot into simulation

## 🖥️ Run RViz Visualization

```bash
source ~/robot_ws/install/setup.bash
ros2 launch robot_description display.launch.py
```

RViz is used to:

* Visualize the robot model
* Inspect coordinate frames
* Verify links and joints
* Monitor TF transformations

## 🌳 TF Tree

```
base_link
├── wheel_left_link
├── wheel_right_link
├── caster_front_link
├── caster_rear_link
└── imu_link
```

## 📊 Project Workflow

1. Design robot using URDF Xacro
2. Define links, joints, and STL meshes
3. Publish transforms using Robot State Publisher
4. Visualize robot in RViz
5. Spawn robot in Gazebo Sim
6. Verify simulation setup

## 🎯 Learning Outcomes

* ROS 2 workspace structure
* URDF Xacro modeling
* TF2 transformations
* Gazebo simulation
* RViz visualization
* ROS 2 launch system
* Robotics simulation workflow

## 🔮 Future Improvements

* ROS 2 Control integration
* Differential drive controller
* Teleoperation support
* SLAM and mapping
* Navigation stack (Nav2)
* Sensor integration

## 🙌 Acknowledgements

Built using ROS 2 ecosystem for learning robot modeling and simulation.
