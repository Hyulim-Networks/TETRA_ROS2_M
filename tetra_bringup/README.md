# 🔧 Tetra Bringup

## 📖 개요
Tetra Bringup 패키지는 Tetra 로봇의 초기화 및 설정을 담당합니다. 이 패키지는 로봇의 기본 설정을 실행합니다.

## 의존성
- ament_cmake
- nav2_common
- navigation2
- launch_ros
- diff_drive_controller
- joint_state_broadcaster
- slam_toolbox
- xacro

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `tetra_bringup` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select tetra_bringup
   ```

## 주요 파일 설명
### launch/
- **`tetra_bringup.launch.py`**: Tetra 로봇의 주요 노드들을 실행하는 launch 파일입니다. EKF 로컬라이제이션, 조이스틱, URDF, 서비스 노드 등을 포함합니다.

### params/
- **`ekf.yaml`**: EKF 로컬라이제이션을 위한 설정 파일로, 주로 로봇의 센서 데이터와 odometry 데이터를 통합하여 위치를 추정합니다.

## 주요 노드
- **`tetra`**: Tetra 로봇의 메인 노드로, 로봇의 구동 및 센서 데이터를 처리합니다.
- **`robot_localization`**: EKF 로컬라이제이션 노드로, odometry와 IMU 데이터를 통합하여 로봇의 위치를 추정합니다.
- **`tetra_interface`**: 로봇의 인터페이스 노드로, 추가적인 하드웨어 옵션을 설정합니다.
- **`iahrs_driver`**: IMU 센서 드라이버 노드로, IMU 데이터를 처리합니다.
- **`joy_node`**: 조이스틱 입력을 처리하는 노드입니다.
- **`robot_state_publisher`**: 로봇의 URDF를 퍼블리시하여 TF 트리를 생성합니다.
- **`tetra_service`**: Tetra 로봇의 서비스 노드로, 다양한 서비스 요청을 처리합니다.
- **`rosbridge_websocket`**: ROS와 웹 클라이언트 간의 통신을 위한 노드입니다.

## 사용 방법
1. Launch 파일 실행:
   ```bash
   ros2 launch tetra_bringup tetra_bringup.launch.py
   ```
2. EKF 로컬라이제이션 설정을 수정하려면 `params/ekf.yaml` 파일을 편집합니다.
3. 조이스틱 입력을 사용하려면 `joy_node`를 활성화합니다.

## EKF 설정 예시
`params/ekf.yaml` 파일의 주요 설정:
- **`frequency`**: EKF 업데이트 주기 (기본값: 50.0 Hz).
- **`map_frame`**: 맵 프레임 이름 (기본값: `map`).
- **`odom_frame`**: 오도메트리 프레임 이름 (기본값: `odom`).
- **`base_link_frame`**: 로봇의 기본 링크 프레임 이름 (기본값: `base_footprint`).
- **`imu0`**: IMU 데이터 토픽 이름 (기본값: `imu/data`).