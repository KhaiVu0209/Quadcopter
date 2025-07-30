1. Ardupilot and Gazebo Plugin 
Step 1 (Terminal 1), run Gazebo:
  gazebo --verbose ~/ardupilot_gazebo/worlds/iris_arducopter_runway.world
Step 2 Terminal 2), run SITL:
  cd ~/ardupilot/ArduCopter/
  sim_vehicle.py -v ArduCopter -f gazebo-iris --console
  mode GUIDED , arm throttle , takeoff .., velocity 1 1 0 , mode RTL , LAND

Phần 1 là kết nối giữa ArduCopter và QGroundControl qua giao thức MAVProxy mở cổng UDP cho phép giao tiếp giữa các ứng dụng đang diễn ra. ArduPilot (SITL) sẽ gửi và nhận MAVLink tới từ plugin trong Gazebo.

2 Như đã nói bên trên thì MAVLink là giao thức truyền thông giữa FCU và thiết bị ngoại vi như:
  Ground Control Station (Mission Planner, QGroundControl)
  Companion Computer (ví dụ: ROS máy tính)
  Các module bên ngoài: gimbal, camera, telemetry
  
MAVROS là một gói ROS (middleware).
Nó là cầu nối giữa:
ROS (node, topic, service…)
MAVLink (giao thức của FCU)

MAVROS có 2 chiều:
  Nhận dữ liệu từ FCU (qua MAVLink) → chuyển sang ROS topic
    Ví dụ: /mavros/imu/data, /mavros/local_position/pose, /mavros/state
Gửi lệnh từ ROS → MAVLink → FCU
    Ví dụ: /mavros/setpoint_position/local → gửi lệnh vị trí bay
            /mavros/cmd/arming → gửi lệnh arm
            /mavros/set_mode → gửi lệnh thay đổi flight mode
