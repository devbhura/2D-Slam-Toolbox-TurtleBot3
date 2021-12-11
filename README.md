# SLAM TOOLBOX ON TURTLEBOT3

The package slam_turtlebot3 implements slam_toolbox on turtlebot3 (in gazebo)
There are for 4 launchfiles for 4 different tasks. 

1. The launchfile `start_slam.launch` spawns turtlebot3 in rviz and in gazebo. It has teleop enabled which allows the user to move in the world loaded in gazebo and map it. One can use w and x keys on the keyboard to set the positive and negative linear velocities and a and d keys to set the positive and negative angular velocities. To launch the launchfile, run `roslaunch slam_turtlebot3 start_slam.launch` in your workspace directory. To save the map created by moving in the loaded world, run `rosrun map_server map_saver -f <filename>` in the directory you want to save the map. 

2. The launchfile `nav_stack.launch` spawns the turtlebot3 in rviz with the map that was created using `start_slam.launch` and gazebo, with amcl from the navigation stack. One can use the 2D pose estimation to match the initial pose of the map and then use the set nav goal in rviz to set the goal pose. amcl should automatically plan and move the robot. To launch the launchfile, run `roslaunch slam_turtlebot3 nav_stack.launch` in your workspace directory.

![Nav Stack Demonstration Video](slam_turtlebot3/videos/nav_stack.gif)

3. The launchfile `slam_stack.launch` spawns the turtlebot3 in rviz. This launchfile implements slam_toolbox and maps the unknown region while navigating. One needs to set the nav goal in rviz to explorable regions of the cost map, and the slam_toolbox plans the path and maps while navigating. To launch the launchfile, run `roslaunch slam_turtlebot3 slam_stack.launch` in your workspace directory.

![Slam Stack Demonstration Video](slam_turtlebot3/videos/slam_stack.gif)

4. Implements slam_toolbox like in part3 but runs a node mover, to make the robot randomly explore the world. The mover node gives an action to the move_base by setting random x,y coordinates. If move_base can execute those coordinates, the position of the robot gets updated and the process repeats itself until shutdown. To launch the launchfile, run `roslaunch slam_turtlebot3 explore_slam.launch` in your workspace directory.

![Explore Demonstration Video](slam_turtlebot3/videos/explore.gif)
