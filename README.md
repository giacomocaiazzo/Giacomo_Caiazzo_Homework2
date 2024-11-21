Repository for Homework 2 of Robotics Labs course completed by Marco Bartone P38000237, Giacomo Caiazzo P38000236, Matteo De Simone P38000232, Nicola Monetti P38000238.

## Robotics Lab - Homework 2

### Overview
This is a report of the Homework 2 of Robotics Lab course using Docker and ROS2 with RVIZ2 and Gazebo. The repo contains the steps to download the folders from github and to run the launch file for the simulations of the builded manipulator robot with the position controller, the joint space inverse dynamic torque controller or in the operational space inverse dynamics torque controller.

### Usage

Open the terminal, open the container and enter into the directory where you want to download the folder, then download it with:

      $ git clone https://github.com/NicoMonetti/Nicola_Monetti_homework2.git

-------------------------------

By default, the launch file run the RVIZ2 and the ROS2 simulations to appreciate the kinematics of the robot with the position controller (with RVIZ2) and the dynamics of the robot with the torque controller (with Gazebo). If you want to launch only the RVIZ2 simulation to appreciate only the kinematics of the robot, open the iiwa.launch.py file and set the default value of the Gazebo simulation (line 80) with "false" value:

-	default_value='false',

--------------------------------

To build the packages, enter into the ROS2 workspace and build them with:

      $ colcon build

Atfer this, use the source command:

      $ source install/setup.bash

Run the simulations of the manipulator robot using the position controller with:

      $ ros2 launch iiwa_bringup iiwa.launch.py

or move to the src/arm_description/launch directory and run the simulations:

      $ cd src/ros2_iiwa/iiwa_bringup/launch
      $ ros2 launch iiwa.launch.py
      
Instead of the previous commands, to use the torque controller launch the simulations with:
 
      $ ros2 launch iiwa_bringup iiwa.launch.py command_interface:="effort" robot_controller:="iiwa_arm_torque_controller"

--------------------------------

Open another terminal, connect to the same docker container and use the following commands in the ROS2 workspace to run the node:

      $ source install/setup.bash
      $ ros2 run ros2_kdl_package ros2_kdl_node


