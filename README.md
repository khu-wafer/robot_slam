# robot_slam

## Summary
This description provides an overview of the autonomous driving part of this project. Prior to the explanation, please note that this project was developed in the following environment: PC with Ubuntu 18.04 LTS and Melodic, Turtlebot3 with Kinetic. It does not guarantee compatibility with other distributions. Additionally, it is assumed that the user has basic knowledge of ROS and has a PC with ROS installed as well as a Turtlebot3. And we uploaded the result of this project. Please refer to this [YouTube video](https://youtu.be/7_lBd4AszNM).

## Set up
1. Install ROS through [the official ROS website](http://wiki.ros.org/Distributions).

2. Prepare the Turtlebot3. If not available, simulation can be used.

## How to Run (Simulation)
1. Launch Roscore.
```
roscore
```

2. Load the virtual environment through Gazebo.
```
roslaunch turtlebot3_gazebo turtlebot3_world.launch
```

3. Create a map through manual control from the Remote PC.
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
```
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_method:=gmapping
```

4. Save the map after completing it.
```
rosrun map_server map_saver -f ~/map
```

5. Load the map for navigation.
```
rosrun map_server map_server map.yaml
```

6. Launch Gmapping.
```
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=${ADDRESS_OF_MAP.yaml}
```

7. Output the robot's position. You can know the poisition of the robot and make the robot to move that position. Please refer to [here](https://github.com/khu-wafer/robot_communication)
```
watch -n 10 rostopic echo /odom
```

## How to Run (Real)
1. Launch Roscore.
```
roscore
```

2-1. Establish a terminal connection with the Turtlebot3.
```
ssh pi@{IP_ADDRESS_OF_TURTLEBOT3}
```

2-2. Launch bringup on the Turtlebot3's terminal.
```
roslaunch turtlebot3_bringup turtlebot3_robot.launch
```

3. Once calibration is complete, create a map from the Remote PC through manual control.
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
```
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_method:=gmapping
```

4. Save the completed map.
```
rosrun map_server map_saver -f ~/map
```

5. Load the map for navigation.
```
rosrun map_server map_server map.yaml
```

6. Launch Gmapping.
```
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=${ADDRESS_OF_MAP.yaml}
```

7. Output the robot's position. You can know the poisition of the robot and make the robot to move that position. Please refer to [here](https://github.com/khu-wafer/robot_communication)
```
watch -n 10 rostopic echo /odom
```

## Credits
[Jinyeob Kim](https://github.com/JinnnK)
