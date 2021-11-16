# Evarobot (ROS Noetic)

This repository includes the Evarobot ROS Noetic packages.

![Image of Evarobot](https://github.com/inomuh/evarobot/blob/main/images/evarobot.png)

- evarobot_description: It is the sub-package containing urdf and mesh files of the Evarobot.
- evarobot_simulation: It is a sub-package containing the package and launch files required for the simulation of the Evarobot.
- evarobot_slam: It is a sub-package containing the slam_gmapping launch files.
- evarobot_navigation: It is a sub-package containing the navigation launch and config files.

![Image of Evarobot Slam](https://github.com/inomuh/evarobot/blob/main/images/evarobot_slam.png)

### For old Evarobot ROS packages: 

https://github.com/inomuh/evapc_ros

https://github.com/inomuh/evarobot_simulator
      
### For more information about Evarobot:
    
http://wiki.ros.org/Robots/evarobot
      
![Image of Evarobot Navigation](https://github.com/inomuh/evarobot/blob/main/images/evarobot_navigation.png)

Launch Command:
---------------

Gazebo Launching:

      Empty World:

          $ roslaunch evarobot_simulation evarobot_gazebo_emptyworld.launch

      Maze World:

            $ roslaunch evarobot_simulation evarobot_gazebo_emptyworld.launch
      
Solo-Rviz Launching:

    $ roslaunch evarobot_simulation evarobot_rviz_standalone.launch
    
Rviz (with Gazebo) Launching:

    $ roslaunch evarobot_simulation evarobot_rviz.launch
    
SLAM Mapping Launching (must work with Gazebo and RViz Launching):

    $ roslaunch evarobot_slam evarobot_slam.launch
    
Navigation Launching:

    $ roslaunch evarobot_navigation evarobot_navigation.launch

![Image of Evarobot Navigation Move](https://github.com/inomuh/evarobot/blob/main/images/evarobot_navigation_move.png)

-----------------------------------------------------------------------------------------------------------------------
Requirements:
-------------
- In order for the "joint_state_publisher" to work, "joint_state_publisher_gui" package must be downloaded to your computer.

        $ sudo apt update
        $ sudo apt install ros-noetic-joint-state-publisher-gui
        
- In order for the "joint_state_controller" to work, "joint_state_controller_gui" package must be downloaded to your computer.

        $ sudo apt install ros-noetic-ros-controllers
       
- In order for the "driver_base" to work, "driver_base" package must be downloaded to your workspace.
        
        $ cd ~/catkin_ws/src
        $ git clone https://github.com/ros-drivers/driver_common -b indigo-devel
        
- In order for the "interactive marker twist server" to work, "interactive_twist_marker_server" package must be downloaded to your workspace.
        
        $ cd ~/catkin_ws/src
        $ git clone https://github.com/ros-visualization/interactive_marker_twist_server -b kinetic-devel
        
- In order for the SLAM to work, "slam_gmapping" package must be downloaded to your workspace.
        
        $ cd ~/catkin_ws/src
        $ git clone https://github.com/ros-perception/slam_gmapping.git -b melodic-devel
        $ sudo apt-get install ros-noetic-openslam-gmapping
        
- In order for the sensors to work properly, "gazebo_ros_pkgs" files must be downloaded to your computer.

        $ sudo apt-get install ros-noetic-gazebo-ros-pkgs
    
- In order for the navigation tools to work properly, "ros-navigation" must be downloaded to your computer.

        $ sudo apt-get install ros-noetic-ros-navigation
        
-------------------------------------------------------------------------------
Changelog:
----------
Update v1.0 - 03.12.20
----------------------
- First version

Update v1.0.1 - 16.11.21
----------------------
- Added new map and Gazebo launch file (map_depo.world) 
        
