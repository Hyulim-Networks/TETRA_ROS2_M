# tetra_navigation2

## 설명
`tetra_navigation2` 패키지는 Tetra 로봇의 내비게이션을 위한 ROS2 설정 및 실행 파일을 제공합니다. 이 패키지는 Behavior Trees, Launch 파일, 매핑 및 파라미터 파일, RViz 설정 등을 포함하여 로봇의 경로 계획, 위치 추정 및 장애물 회피를 지원합니다.

## 의존성
- ament_cmake
- nav2_bringup

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `tetra_navigation2` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select tetra_navigation2
   ```

## 구성 요소
### Behavior Trees
- **`navigate_through_poses_w_replanning_and_recovery.xml`**: 여러 목표 지점을 경유하며 경로를 계획하고 복구 동작을 수행하는 Behavior Tree.
- **`navigate_to_pose_w_replanning_and_recovery.xml`**: 단일 목표 지점으로 이동하며 경로를 계획하고 복구 동작을 수행하는 Behavior Tree.

### Launch 파일
- **`bringup_launch.py`**: 로봇의 전체 시스템을 실행하는 Launch 파일.
- **`localization_launch.py`**: 로봇의 위치 추정을 위한 Launch 파일.
- **`navigation_launch.py`**: 내비게이션을 실행하는 Launch 파일.
- **`rviz_launch.py`**: RViz를 실행하여 로봇의 상태를 시각화하는 Launch 파일.
- **`slam_launch.py`**: SLAM(Simultaneous Localization and Mapping)을 실행하는 Launch 파일.
- **`tetra_navigation.launch.py`**: 내비게이션과 관련된 모든 설정을 포함한 메인 Launch 파일.

### 매핑 및 파라미터 파일
- **Maps**:
  - `office.yaml`, `office.pgm`: 사무실 환경의 맵 파일.
  - `71052860-0627-11f0-93f0-13ab0628bab1.yaml`, `71052860-0627-11f0-93f0-13ab0628bab1.pgm`: 특정 환경의 맵 파일.
- **Params**:
  - `amcl_localization.yaml`: 위치 추정을 위한 AMCL 파라미터 파일.
  - `navigation.yaml`: 내비게이션 설정을 위한 파라미터 파일.

### RViz 설정
- **`tetra_navigation2.rviz`**: RViz에서 로봇의 상태를 시각화하기 위한 설정 파일.

## 사용 방법
1. 내비게이션 실행:
   ```bash
   ros2 launch tetra_navigation2 tetra_navigation.launch.py
   ```
2. RViz 실행:
   ```bash
   ros2 launch tetra_navigation2 rviz_launch.py
   ```
3. SLAM 실행:
   ```bash
   ros2 launch tetra_navigation2 slam_launch.py
   ```

## 참고
- ROS2 내비게이션2 공식 문서: [https://navigation.ros.org/](https://navigation.ros.org/)
- ROS2 공식 문서: [https://docs.ros.org/en/foxy/](https://docs.ros.org/en/foxy/)
