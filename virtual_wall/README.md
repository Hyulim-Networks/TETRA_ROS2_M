# virtual_wall

## 설명
`virtual_wall` 패키지는 ROS2 기반으로 가상 벽(virtual wall)을 생성하고 관리하기 위한 기능을 제공합니다. 이 패키지는 가상 장애물을 추가하거나 제거할 수 있는 서비스를 제공하며, 로봇의 경로 계획 및 장애물 회피를 지원합니다.

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
- pcl_ros
- libpcl-dev
- rosidl_default_runtime

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `virtual_wall` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select virtual_wall
   ```

## 주요 구성 요소
### 노드
- **`virtual_wall_node`**: 가상 벽을 생성하고 관리하는 주요 노드로, `virtual_wall.launch.py`를 통해 실행됩니다.

### 서비스
- **`/add_virtual_wall_cmd`** (`AddVirtualWall.srv`):
  - 가상 벽을 추가하거나 제거하는 서비스.
  - 요청 필드:
    - `polygons`: 추가할 다각형의 배열.
    - `ids`: 다각형에 대한 고유 ID 배열.
    - `remove`: 다각형을 제거할지 여부를 나타내는 플래그.
  - 응답 필드:
    - `success`: 요청 성공 여부.
    - `message`: 요청 결과에 대한 메시지.

### 주요 토픽
- **`/Global_virtual_wall`**: 전역 가상 벽 데이터를 퍼블리시하는 `sensor_msgs/msg/PointCloud2` 타입의 토픽.
- **`/Local_virtual_wall`**: 로컬 가상 벽 데이터를 퍼블리시하는 `sensor_msgs/msg/PointCloud2` 타입의 토픽.

## 사용 방법
1. Launch 파일 실행:
   ```bash
   ros2 launch virtual_wall virtual_wall.launch.py
   ```
2. 가상 벽 추가 예제:
   ```bash
   ros2 service call /add_virtual_wall_cmd virtual_wall/srv/AddVirtualWall "{polygons: [
     {points: [{x: 0.5, y: 1.0, z: 0.0}, {x: 1.5, y: 0.5, z: 0.0}, {x: 1.5, y: 1.5, z: 0.0}, {x: 1.0, y: 1.5, z: 0.0}]},
     {points: [{x: 0.0, y: 2.0, z: 0.0}, {x: 1.0, y: 2.0, z: 0.0}, {x: 1.0, y: 2.5, z: 0.0}, {x: 0.0, y: 2.5, z: 0.0}]}
   ], ids: [1, 2], remove: false}"
   ```
3. 가상 벽 제거 예제:
   ```bash
   ros2 service call /add_virtual_wall_cmd virtual_wall/srv/AddVirtualWall "{ids: [2], remove: true}"
   ```

## 참고
- ROS2 공식 문서: [https://docs.ros.org/en/foxy/](https://docs.ros.org/en/foxy/)

