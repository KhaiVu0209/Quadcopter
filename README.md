1. Ardupilot and Gazebo Plugin 

Step 1 (Terminal 1), run Gazebo:
  gazebo --verbose ~/ardupilot_gazebo/worlds/iris_arducopter_runway.world
  
Step 2 Terminal 2), run SITL:
  cd ~/ardupilot/ArduCopter/
  sim_vehicle.py -v ArduCopter -f gazebo-iris --console
  mode GUIDED , arm throttle , takeoff .., velocity 1 1 0 , mode RTL , LAND

Phần 1 là kết nối giữa ArduCopter và QGroundControl qua giao thức MAVProxy mở cổng UDP cho phép giao tiếp giữa các ứng dụng đang diễn ra. ArduPilot (SITL) sẽ gửi và nhận MAVLink tới từ plugin trong Gazebo.
