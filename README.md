# nanny_navigation

<h3>Launch Files:</h3>
Nanny_mapping-

Nanny_move_base
This launches the costmaps, move_base, and base local planner yaml files. In RViz, you should be able to see the local and global costmaps by selecting their topics in the map type and be able to set a goal for the robot to move to using the 2D Nav Goal. This may need some work. To launch this file, you can run:
roslaunch nanny_navigation nanny_move_base.launch


Nanny_navigation-

<h3>Config Files: </h3>
http://wiki.ros.org/navigation/Tutorials/RobotSetup

Base_local_planner_params.yaml
The base local planner is used to generate the velocity commands to the robot. It sets the max and min velocities for the robot. Since our robot is differential, it is non-holonomic.

Costmap_common_params.yaml
This file points the costmaps at the right sensors to detect obstacles properly. We set the  obstacle_range how far away an obstacle needs to be for the costmap to detect it. We also set the footprint of the robot.
Global_costmap_params.yaml
This file defines the transformation between the map and the robot and uses the static map to see whether a map or the map server is used to initialize the costmap. It is used for global planning, creating long-term plans over the entire environment.

Gmapping_params.yaml

Local_costmap_params.yaml
This file uses the odom as the global frame and is used for local planning and obstacle avoidance.

Localization_params.yaml

Move_base_params.yaml
This creates an action that given a goal in the world, it will try to move the robot to that spot. It contains the two costmaps and links together with the global and local planner to accomplish a task.

Global planner
http://wiki.ros.org/navigation/Tutorials/Writing%20A%20Global%20Path%20Planner%20As%20Plugin%20in%20ROS#Testing_the_planner_with_RVIZ
Written so that we can call out specific coordinates in the map to route to.
Global_planner.cpp
Global_planner.h

Controller VFH
Controller VFH is a navigation algorithm that lives inside of MATLAB then a connection is made to the ROS network on the robot. The vector field histogram (VFH) algorithm computes obstacle-free steering directions for a robot based on range sensor readings. Range sensor readings are used to compute polar density histograms to identify obstacle location and proximity. Based on the specified parameters and thresholds, these histograms are converted to binary histograms to indicate valid steering directions for the robot. The VFH algorithm factors in robot size and turning radius to output a steering direction for the robot to avoid obstacles and follow a target direction.

