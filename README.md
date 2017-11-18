# My robot model Pionner

This repo is intended to work as a tutorial for starting to work with ros + gazebo. 
It has a launch file with the pionner model working with lidar in world scenario.  


## Requiremets 

- ros & gazebo 

## Tutorial

Create catkin workspace 
```
mkdir -p ~/pioneer_sim/src 
cd ~/pioneer_sim/src 
catkin_init_workspace 
cd ~/pioneer_sim 
catkin_make install 
```
Clone this repo & amr robots & gazebo ros demo: 
```
cd ~/pioneer_sim/src/
git clone https://github.com/IgnacioCarlucho/my_robot_model_pioneer
git clone https://github.com/MobileRobots/amr-ros-config
https://github.com/ros-simulation/gazebo_ros_demos
```
amr-robots has the pionner model, meshes, etc. while ros demo has the mesh used for lidar and the cameras. 

do catkin make and source 

```
cd ~/pioneer_sim
catkin_make
source devel/setup.bash
```

## explanation 

to run we need to do: 
```
cd src/my_robot_model_pioneer/launch
roslaunch robot.launch
```
This runs an empty world + the includes in the file "/world/myrobot_world".
And spawns the pioneer's urdf model in this world.    
Now by doing 
```
rostopic list
```
we can see the rosaria topics and the sonars. If you wanna change the topics names or modify parameters of the configuration, that can be done in the urdf file. 

Pionner model is a urdf file. It is automatically generated from a xacro file. If you modify the xacro then you have to generate the urdf by doing:   
```
rosrun xacro xacro --inorder -o model.urdf model.urdf.xacro
```
### Plotting: 

You can send velocity commands by doing: 
```
rostopic pub /sim_p3at/cmd_vel geometry_msgs/Twist '[0.1, 0.0, 0.0]' '[0.0, 0.0, 0.0]'
```
There is also an amazing tool for real time plotting, rqt plot, to plot for instance the velocity of the robot: 
```
rqt_plot /sim_p3at/odom/twist/twist/linear/x:y:z
```
while the velocity is: 
```
rqt_plot /sim_p3at/odom/pose/pose/position/x:y:z
```
There is another plotting tool, Rviz, that allows you to see the laser points in real time. 
transform the laser: 

run rviz: 


how to subscribe and publish on python??? 
also on the talk you should explain how to modify the model. ( maybe show uwsim)