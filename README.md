# 🌟 TETRA-DS5_ROS2-jazzy 버전

## 🛠️ 개요
TETRA-DS5 ROS2 패키지는 다양한 센서와 ROS2 기반의 기능을 통합하여 로봇 관제 및 제어를 지원합니다. 이 패키지는 ROS2 Jazzy 버전을 기반으로 하며, 다음과 같은 센서를 지원합니다:

- **SICK Tim571**: 2D LiDAR ([🔗 GitHub 링크](https://github.com/SICKAG/sick_scan_xd))
- **Cygbot D1**: 소형 2D/3D LiDAR ([🔗 GitHub 링크](https://github.com/CygLiDAR-ROS/cyglidar_d1))
- **Cygbot D2**: 고성능 2D/3D LiDAR
- **Realsense D455**: 3D Depth Camera ([🔗 GitHub 링크](https://github.com/IntelRealSense/realsense-ros))
- **IAHRS**: IMU ([🔗 GitHub 링크](https://github.com/wookbin/iahrs_driver_ros2))

## 📦 패키지 구성

### 1. 🏷️ apriltag_ros2
- **기능**: AprilTag 기반의 태그 감지 및 위치 추정.
- **주요 파일**:
  - 📄 `apriltag_detection.launch.py`: 태그 감지 실행을 위한 launch 파일.
  - 📂 `src/`: 태그 감지 및 위치 추정 관련 소스 코드.

### 2. 📡 cyglidar_d1-ROS2-v0.3.0
- **기능**: Cygbot D1 LiDAR 데이터 수집 및 처리.
- **주요 파일**:
  - 📄 `D1_Publisher.cpp`: LiDAR 데이터 퍼블리싱.
  - 🚀 `cyglidar.launch.py`: LiDAR 실행을 위한 launch 파일.

### 3. 📡 cyglidar_d2
- **기능**: Cygbot D2 LiDAR 데이터 수집 및 처리.
- **주요 파일**:
  - 📄 `main.cpp`: LiDAR 데이터 처리 메인 코드.
  - 🚀 `cyglidar.launch.py`: LiDAR 실행을 위한 launch 파일.

### 4. 🧭 iahrs_driver
- **기능**: IAHRS IMU 데이터 수집 및 퍼블리싱.
- **주요 파일**:
  - 📄 `iahrs_driver.cpp`: IMU 데이터 처리.
  - 🚀 `iahrs_driver.launch.py`: IMU 실행을 위한 launch 파일.

### 5. 🧩 interfaces
- **기능**: ROS2 메시지 및 서비스 정의.
- **주요 파일**:
  - 📂 `msg/`: ROS2 메시지 정의.
  - 📂 `srv/`: ROS2 서비스 정의.

### 6. 🎥 realsense-ros
- **기능**: Realsense D455 카메라 데이터 수집 및 처리.
- **주요 파일**:
  - 🚀 `rs_launch.py`: 카메라 실행을 위한 launch 파일.
  - 📂 `src/`: 카메라 데이터 처리 소스 코드.

### 7. 📡 sick_scan_xd-develop
- **기능**: SICK LiDAR 데이터 수집 및 처리.
- **주요 파일**:
  - ⚙️ `SickScan.cfg`: LiDAR 설정 파일.
  - 🚀 `launch/`: LiDAR 실행을 위한 launch 파일.

### 8. 🤖 tetra
- **기능**: Tetra 로봇의 기본 제어 기능 제공.
- **주요 파일**:
  - 📄 `tetra.cpp`: 로봇 제어 메인 코드.
  - 🚀 `tetra.launch.py`: 로봇 실행을 위한 launch 파일.

### 9. 🔧 tetra_bringup
- **기능**: Tetra 로봇의 초기화 및 설정.
- **주요 파일**:
  - 🚀 `tetra_bringup.launch.py`: 초기화 실행 파일.
  - ⚙️ `ekf.yaml`: EKF 설정 파일.

### 10. 🗺️ tetra_cartographer
- **기능**: SLAM 및 지도 생성.
- **주요 파일**:
  - 🚀 `cartographer.launch.py`: SLAM 실행 파일.
  - 🖼️ `tetra_cartographer.rviz`: RViz 설정 파일.

### 11. 🛠️ tetra_description
- **기능**: Tetra 로봇의 URDF 및 시뮬레이션 설정.
- **주요 파일**:
  - 📝 `tetra.xacro`: 로봇 URDF 파일.
  - 🚀 `tetra_description.launch.py`: 시뮬레이션 실행 파일.

### 12. 🔌 tetra_interface
- **기능**: Tetra 로봇의 인터페이스 제어.
- **주요 파일**:
  - 📄 `tetra_interface.cpp`: 인터페이스 제어 코드.
  - 🚀 `tetra_interface.launch.py`: 실행 파일.

### 13. 🗺️ tetra_navigation2
- **기능**: 네비게이션 및 경로 계획.
- **주요 파일**:
  - 🚀 `navigation_launch.py`: 네비게이션 실행 파일.
  - 🖼️ `tetra_navigation2.rviz`: RViz 설정 파일.

### 14. 🛠️ tetra_service
- **기능**: Tetra 로봇의 서비스 관리.
- **주요 파일**:
  - 📄 `tetra_service.cpp`: 서비스 처리 코드.
  - 🚀 `tetra_service.launch.py`: 실행 파일.

### 15. 🎥 usb_cam-ros2
- **기능**: USB 카메라 데이터 수집 및 처리.
- **주요 파일**:
  - 📄 `usb_cam_node.cpp`: 카메라 데이터 처리 코드.
  - 🚀 `camera.launch.py`: 실행 파일.

### 16. 🧱 virtual_wall
- **기능**: 가상 벽 생성 및 관리.
- **주요 파일**:
  - 📄 `virtual_wall.cpp`: 가상 벽 처리 코드.
  - 🚀 `virtual_wall.launch.py`: 실행 파일.

## 🛠️ 설치 방법
1. ROS2 Jazzy 설치.
2. 의존성 패키지 설치:
   ```bash
   rosdep install --from-paths src --ignore-src -r -y
   ```
3. 워크스페이스 빌드:
   ```bash
   colcon build
   ```

## 🚀 실행 방법
1. 각 패키지의 launch 파일 실행:
   ```bash
   ros2 launch <패키지명> <launch 파일명>
   ```
2. 예시:
   ```bash
   ros2 launch tetra_service tetra_service.launch.py
   ```

