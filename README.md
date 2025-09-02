# diffdrive_mapping_showcase
A showcase of my differential drive mapping and path planning robot


## Purpose:

This project is intended to facilitate learning of full-stack mobile robotics development with a focus on sensor input, mapping, path planning and control algorithms.
This project is completed without the use of pre-built stacks, such as Nav2, SLAM toolbox or Cartographer. 
This project is a WIP, and as such, the showcase will lay bare not only successes but a number of learning opportunities.


## Current Features:

-Custom occupancy grid: hierarchical breakdown and combining if all cell states agree. Confidence scoring applied to protect from single scan inaccuracies.
-LIDAR integration: Rays traced into quadtree, updating cells as OCCUPIED or UNOCCUPIED as detected. 
-ROS2/Gazebo integration: Publishes occupancy grid to /map, subscribes to /scan


## Known Bugs:

-Robot model slides backwards: expect errors in SDF assignment of joint characteristics
-Occupancy Map grid misses one cell per quad: Believe it is an error in recurssion causing one cell to be 'skipped' during assignment
-Occupancy Map update conficence scores aren't triggering as before, leading to increased inaccuracy and instability of map, although combining issue has been resolved


## Future Actions:

-Bug fixes in mapping (Occupancy Map stability)
-Bug fix in SDF model causing sliding
-Full integration of Mapping, Path Planning and Control


## Current Results: 

-Occupancy grid updates with Black = Occupied, White = Unoccupied, Blue = Unknown. Missing cell per group is preventing attainable path planning and robot control for two reasons: 
First, the required accuracy to follow a path on the max-resolution grid is unattainable by the robot - it would constantly need to recalculate path from it's location. Wheels would not 
spin in small enough incriments to maintain robot location along max-resolution grid size. Second, the path planner (modified A* planner) takes into account cell distance from obstacles to
ensure the robot never approaches close enough to collide. At max resolution, only the closest cells to an obstacle carry that penalty, so the planner would likely favor a path that would
cause a collision.


## Showcase files:

basic_demo_edited.mp4: Demonstrates robot motion in Gazebo with Rviz output map of Occupancy Grid. Edited for time.
Status Report.pdf: In depth report of the project.
