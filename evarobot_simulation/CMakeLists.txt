cmake_minimum_required(VERSION 3.0.2)
project(evarobot_simulation)

find_package(catkin REQUIRED COMPONENTS
  urdf
  message_generation 
  gazebo_msgs 
  roscpp 
  rospy 
  nodelet 
  angles 
  std_srvs 
  geometry_msgs 
  sensor_msgs 
  nav_msgs 
  urdf 
  tf 
  tf2_ros 
  dynamic_reconfigure 
  driver_base 
  rosgraph_msgs 
  trajectory_msgs 
  image_transport 
  rosconsole
  cv_bridge
  polled_camera
  camera_info_manager
  interactive_marker_twist_server
)

include (FindPkgConfig)
if (PKG_CONFIG_FOUND)
  pkg_check_modules(XML libxml-2.0)
  pkg_check_modules(OGRE OGRE)
  pkg_check_modules(OGRE-Terrain OGRE-Terrain)
  pkg_check_modules(OGRE-Paging OGRE-Paging)
else()
  message(FATAL_ERROR "pkg-config is required; please install it")
endif()

# Depend on system install of Gazebo and SDFormat
find_package(gazebo REQUIRED)
find_package(Boost REQUIRED COMPONENTS thread)

execute_process(COMMAND
  pkg-config --variable=plugindir OGRE
  OUTPUT_VARIABLE OGRE_PLUGIN_PATH
  OUTPUT_STRIP_TRAILING_WHITESPACE
)


generate_dynamic_reconfigure_options(
  cfg/CameraSynchronizer.cfg
  cfg/GazeboRosCamera.cfg
  cfg/GazeboRosOpenniKinect.cfg
  cfg/Hokuyo.cfg
  cfg/SensorModel.cfg
)

include_directories(include
  ${Boost_INCLUDE_DIRS}
  ${catkin_INCLUDE_DIRS}
  ${OGRE_INCLUDE_DIRS}
  ${OGRE-Terrain_INCLUDE_DIRS}
  ${OGRE-Paging_INCLUDE_DIRS}
  include
  hector_gazebo_plugins
)

link_directories(
  ${OGRE_LIBRARY_DIRS}
  ${OGRE-Terrain_LIBRARY_DIRS}
  ${OGRE-Paging_LIBRARY_DIRS}
)

catkin_package(
  )

add_dependencies(${PROJECT_NAME}_gencfg ${catkin_EXPORTED_TARGETS})



include_directories(
  ${catkin_INCLUDE_DIRS}
)


install(DIRECTORY include/
   DESTINATION ${CATKIN_GLOBAL_INCLUDE_DESTINATION}
   FILES_MATCHING PATTERN "*.h"
)

foreach(dir cfg launch map worlds)
    install(DIRECTORY ${dir}/
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach()
