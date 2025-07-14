# Quadcopter
PX4 AutoPilot 
- open firmware for drone, use for simulate and real
- It can be combine with gazebo to simulate
MARVOS
- It is ROS pkg
- A bridge link, communation PX4 and ROS

Run :
Terminal 1 : 
cd ~/PX4-Autopilot
make px4_sitl_default gazebo

Terminal 2 :
roslaunch mavros px4.launch fcu_url:="udp://:14540@127.0.0.1:14557"

Terminal 3 :
cd ~/catkin_ws
source devel/setup.bash
roslaunch offb main.launch
