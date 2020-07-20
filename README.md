# PART ONE: RUN THE CODE

Show how to run the code.

## Dependency

ROS and Gazebo

- ROS-melodic (Choose your )
- Gazebo-9.0

Remember to match ROS and Gazebo distribution. Details [here](http://gazebosim.org/tutorials?tut=ros_wrapper_versions&cat=connect_ros)  

Other ROS packages

- ros-melodic-turtlebot3
- ros-melodic-robot-state-publisher
- ros-melodic-joint-state-publisher-gui

## RUN

```bash
# Open a terminal
./build.sh
source devel_isolated/setup.bash
roslaunch robot_gz show_in_gazebo.launch
# Open a new terminal
source devel_isolated/setup.bash
roslaunch robot_gz show_in_rviz.launch
# Open a new terminal to control the robot
# Package Turtlebot3 need a enviromental variable in their launch file
export TURTLEBOT3_MODEL="burger"
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

Or you want to use turtlebot1's way to control the robot.

Source code here: [link](https://github.com/turtlebot/turtlebot) , build it as a ROS package. 

```bash
source <Path2SetupBash>/setup.bash
roslaunch turtlebot_teleop keyboard_teleop.launch
```

Personally, I prefer `turtlebot_teleop` .



---

# PART TWO: Robot Simulation

Use gazebo_ros to do this simulation for washing-floor robot

Here documents how to finishe this simulation in several steps.



## 01. Geometry Model

Read [URDF in Gazebo](http://gazebosim.org/tutorials?tut=ros_urdf&cat=connect_ros) 

Learn how to add \<gazebo\> element in `.xacro` .



## 02. Gazebo_ros Plugin

I learn how to use gazebo_ros plugin from an example of several Turtlebot3 ros package below:

-  [turtlebot3](https://github.com/ROBOTIS-GIT/turtlebot3) 
-  [turtlebot3_applications](https://github.com/ROBOTIS-GIT/turtlebot3_applications) 
-  [turtlebot3_simulations](https://github.com/ROBOTIS-GIT/turtlebot3_simulations) 
-  [turtlebot3_msgs](https://github.com/ROBOTIS-GIT/turtlebot3_msgs) 

Clone them in the same directory and `catkin_make` to build the code

Alternatively, you can install them in ROS by `apt-get install` 

Do not forget to install `ros-melodic-`

```bash
# view the turtlebot3 in gazebo
roslaunch turtlebot3_gazebo turtlebot3_world.launch

# view the turtlebot3 in rviz
roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch

# use teleop to control the turtlebot
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

Read the source code of these packages

It shows how to use `libgazebo_ros_diff_drive.so` to implement the differential speed control.

Also, it provides the examples of  `libgazebo_ros_imu.so` and `libgazebo_ros_laser.so` 



## 03. Simplify by Macro

 `.xacro` is much powerful than `.urdf` for its macros.

Use macros can simplify model written in `.urdf` or `.xacro` .

Tutorial for all. [Click here](http://wiki.ros.org/xacro#Math_expressions) 



## 04. Auto Generate Model

Write a cpp library to read the config of robot including sensor extrinsic, intrinsic



## 05. Adapt the Simulation 

Adapt the simulation to the [Tonglu](http://www.tonglurobot.com/) Intelligent Driving system named `Tergeo` .

This part will not be include in this repository.

