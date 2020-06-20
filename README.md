# Localization of Mobile Robot

## Description
The aim of this project is to use the ROS Adaptive Monte Carlo Localization (AMCL) package in order to localize a mobile robot using laser sensor data from odometry and laser scan readings. 

## Setup
### Cloning to catkin workspace
In a ROS environment, initally run the following commands to set up catkin_workspace:
```
$ mkdir -p /home/$USER/catkin_ws/src
$ cd /home/$USER/catkin_ws/src
$ catkin_init_workspace
$ cd ..
$ catkin_make
```
Enter the `/home/$USER/catkin_ws/src` directory and clone the repository `git clone git@github.com:onurbagoren/localization.git` 
### Execution
#### Launching the nodes
In order to run the program, initially source the catkin workspace by running the following commands:
```
$ cd /home/$USER/catkin_ws/
$ source deve/setup.bash
```
and then launch the AMCL node by running
```
$ roslaunch localization amcl.launch
```

On a different terminal, while the first one is running, source the catkin workspace and run
```
$ roslaunch localization world.launch
```

#### Driving and localizing the robot
In order to drive the robot, there are two available options

1. **Option 1: Sending a 2D Nav Goal through RVIz**
   On the RViz window tha appears, select the 2D Nav Goal option, click on a location and select an orientation. The robot should drive towards this goal.
2. **Option 2: Driving through teleop commands**:
   Open a new terminal and source the catkin_workspace. Run the following command in order to drive the robot throug keyboard commands:
   ```
   rosrun teleop_twist_keyboard teleop_twist_keyboard.py
   ```
   Follow the commands that appear on the screen to drive the robot.

## Potential Errors and Fixing
### Missing packages
Not every ROS ditribution comes with ethe amcl, map_server and move_base packages. After launching the amcl node, if there are errors regarding the `amcl`, `map_server` or `move_base` packages, run the following command on the terminal:
```
sudo apt-get install ros-<DISTRIBUTION>-<PACKAGE_NAME>
```

#### Screenshot of localization
![Localization](/home/onurbagoren/catkin_ws/src/localization/localization.png)