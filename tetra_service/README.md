# tetra_service

## 설명
`tetra_service` 패키지는 Tetra 로봇의 다양한 기능을 제어하고 관리하기 위한 ROS2 기반 서비스 노드를 제공합니다. 이 패키지는 로봇의 도킹, 맵 관리, 위치 설정 및 이동 명령과 같은 주요 기능을 지원합니다.

## 의존성
- ament_cmake
- rclcpp
- rmw_implementation
- std_msgs
- std_srvs
- sensor_msgs
- tf2
- tf2_ros
- geometry_msgs
- nav_msgs
- pcl_ros
- libpcl-dev
- apriltag_msgs
- apriltag
- interfaces

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `tetra_service` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select tetra_service
   ```

## 주요 구성 요소
### 노드
- **`tetra_service`**: 로봇의 다양한 서비스를 제공하는 주요 노드로, `tetra_service.launch.py` 또는 `tetra_service_launch.xml`을 통해 실행됩니다.

### 서비스
- **`/docking_cmd`**: 도킹을 제어합니다.
- **`/docking_stop_cmd`**: 도킹을 중지합니다.
- **`/save_map_cmd`**: 현재 맵을 저장합니다.
- **`/delete_map_cmd`**: 저장된 맵을 삭제합니다.
- **`/run_mapping_cmd`**: 맵핑을 시작합니다.
- **`/run_navigation_cmd`**: 내비게이션을 시작합니다.
- **`/get_information_cmd`**: 로봇의 정보를 가져옵니다.
- **`/set_location_cmd`**: 로봇의 위치를 설정합니다.
- **`/goto_location_cmd`**: 특정 위치로 이동합니다.
- **`/goto_location2_cmd`**: 특정 위치로 이동(옵션 포함).
- **`/goto_cancel_cmd`**: 이동 명령을 취소합니다.
- **`/set_maxspeed_cmd`**: 로봇의 최대 속도를 설정합니다.

### 토픽
#### 발행되는 토픽
- **`/cmd_vel_manual`** (`geometry_msgs/msg/Twist`): 수동 속도 명령을 퍼블리시합니다.
- **`/pose_reset`** (`std_msgs/msg/Int32`): 위치 초기화 신호를 퍼블리시합니다.
- **`/initialpose`** (`geometry_msgs/msg/PoseWithCovarianceStamped`): 초기 위치를 퍼블리시합니다.
- **`/movebase`** (`std_msgs/msg/Int32`): 이동 명령 상태를 퍼블리시합니다.
- **`/footprint`** (`geometry_msgs/msg/Pose`): 로봇의 발자국 위치를 퍼블리시합니다.

#### 구독되는 토픽
- **`/detections`** (`apriltag_msgs/msg/AprilTagDetectionArray`): AprilTag 감지 데이터를 구독합니다.
- **`/scan`** (`sensor_msgs/msg/LaserScan`): 레이저 스캔 데이터를 구독합니다.
- **`/scan2`** (`sensor_msgs/msg/LaserScan`): 두 번째 레이저 스캔 데이터를 구독합니다.
- **`/bumper_data`** (`std_msgs/msg/Int32`): 범퍼 데이터를 구독합니다.
- **`/emg_state`** (`std_msgs/msg/Int32`): 비상 정지 상태를 구독합니다.
- **`/tetra_battery`** (`std_msgs/msg/Int32`): 배터리 상태를 구독합니다.
- **`/docking_status`** (`std_msgs/msg/Int32`): 도킹 상태를 구독합니다.
- **`/conveyor_sensor`** (`std_msgs/msg/Int32`): 컨베이어 센서 데이터를 구독합니다.
- **`/conveyor_movement`** (`std_msgs/msg/Int32`): 컨베이어 이동 상태를 구독합니다.
- **`/joy`** (`sensor_msgs/msg/Joy`): 조이스틱 입력을 구독합니다.
- **`/particle_cloud`** (`nav2_msgs/msg/ParticleCloud`): 파티클 필터 데이터를 구독합니다.
- **`/cmd_vel`** (`geometry_msgs/msg/Twist`): 속도 명령을 구독합니다.
- **`/initialpose`** (`geometry_msgs/msg/PoseWithCovarianceStamped`): 초기 위치를 구독합니다.
- **`/map`** (`nav_msgs/msg/OccupancyGrid`): 맵 데이터를 구독합니다.

## 사용 방법
1. Launch 파일 실행:
   ```bash
   ros2 launch tetra_service tetra_service.launch.py
   ```
2. 서비스 호출 예제:
   - LED 제어:
     ```bash
     ros2 service call /led_cmd interfaces/srv/LedControl "{id: 1, state: true}"
     ```
   - 맵 저장:
     ```bash
     ros2 service call /save_map_cmd interfaces/srv/SaveMap "{map_name: 'office_map'}"
     ```
   - 특정 위치로 이동:
     ```bash
     ros2 service call /goto_location_cmd interfaces/srv/GotoLocation "{location_name: 'charging_station'}"
     ```

## 참고
- ROS2 공식 문서: [https://docs.ros.org/en/foxy/](https://docs.ros.org/en/foxy/)
