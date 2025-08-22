# 🧭 iahrs_driver

## 📖 설명
IAHRS 센서를 위한 ROS2 드라이버 패키지입니다. 이 패키지는 센서 데이터를 수집하고, IMU 데이터를 퍼블리시하며, TF 변환을 브로드캐스트합니다.

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
- interfaces

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `iahrs_driver` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select iahrs_driver
   ```

## 토픽 및 서비스 리스트
- **출력 토픽**:
  - `/imu/data` (타입: `sensor_msgs/Imu`): IMU 데이터를 퍼블리시합니다.
- **서비스**:
  - `/euler_angle_reset` (타입: `interfaces/srv/ImuReset`): 오일러 각도를 초기화합니다.

## 사용 방법 예시
1. Launch 파일 실행:
   ```bash
   ros2 launch iahrs_driver iahrs_driver.launch.py
   ```
2. IMU 데이터를 확인하거나 `/euler_angle_reset` 서비스를 호출하여 오일러 각도를 초기화합니다.

## 주요 기능
- IMU 데이터를 `/imu/data` 토픽으로 퍼블리시.
- TF 변환을 브로드캐스트하여 로봇의 위치와 자세를 제공합니다.
- `/euler_angle_reset` 서비스를 통해 오일러 각도를 초기화할 수 있습니다.

## 코드 구조
- **`src/iahrs_driver.cpp`**: 주요 노드 구현 파일로, 센서 데이터 처리 및 ROS2 통신을 담당합니다.
- **`launch/iahrs_driver.launch.py`**: 노드를 실행하기 위한 Launch 파일입니다.

## 📂 주요 파일
- 📄 `iahrs_driver.cpp`: IMU 데이터 처리 코드.
- 🚀 `iahrs_driver.launch.py`: IMU 실행을 위한 launch 파일.

## 🚀 실행 방법
1. Launch 파일 실행:
   ```bash
   ros2 launch iahrs_driver iahrs_driver.launch.py
   ```