# 🗺️ Tetra Cartographer

## 📖 개요
`tetra_cartographer` 패키지는 Tetra 로봇의 SLAM(Simultaneous Localization and Mapping)을 위한 Cartographer 설정 및 실행 파일을 제공합니다. 이 패키지는 2D SLAM을 지원하며, 로봇의 라이다 데이터를 활용하여 실시간으로 지도를 생성합니다.

## 의존성
- ament_cmake
- cartographer_ros

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `tetra_cartographer` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select tetra_cartographer
   ```

## 📂 주요 파일 설명
### config/
- **`tetra_lds_2d.lua`**: Cartographer의 2D SLAM 설정 파일로, 라이다 데이터 처리 및 지도 생성에 필요한 매개변수를 정의합니다.
- **`tetra_lds_2d(old).lua`**: 이전 버전의 Cartographer 설정 파일로, 참고용으로 제공됩니다.

### launch/
- **`cartographer.launch.py`**: Cartographer 노드를 실행하는 launch 파일로, SLAM을 시작합니다.
- **`occupancy_grid.launch.py`**: Occupancy Grid를 생성하고 퍼블리시하는 노드를 실행하는 launch 파일입니다.

### rviz/
- **`tetra_cartographer.rviz`**: RViz 설정 파일로, SLAM 결과를 시각화하는 데 사용됩니다.

## 주요 노드
- **`cartographer_node`**: Cartographer의 메인 노드로, 라이다 데이터를 처리하여 지도를 생성합니다.
- **`cartographer_occupancy_grid_node`**: Occupancy Grid를 생성하고 퍼블리시하는 노드입니다.

## 🚀 실행 방법
1. SLAM 실행:
   ```bash
   ros2 launch tetra_cartographer cartographer.launch.py
   ```
2. Occupancy Grid 퍼블리시:
   ```bash
   ros2 launch tetra_cartographer occupancy_grid.launch.py
   ```
3. RViz를 사용하여 SLAM 결과를 시각화하려면 `rviz/tetra_cartographer.rviz` 파일을 로드합니다.

## 주요 설정
### `tetra_lds_2d.lua`
- **`map_frame`**: 생성된 지도의 프레임 이름 (기본값: `map`).
- **`tracking_frame`**: 로봇의 추적 프레임 이름 (기본값: `base_footprint`).
- **`published_frame`**: 퍼블리시되는 프레임 이름 (기본값: `odom`).
- **`TRAJECTORY_BUILDER_2D.min_range`**: 라이다의 최소 범위 (기본값: 0.05m).
- **`TRAJECTORY_BUILDER_2D.max_range`**: 라이다의 최대 범위 (기본값: 20.0m).
- **`TRAJECTORY_BUILDER_2D.use_online_correlative_scan_matching`**: 온라인 스캔 매칭 사용 여부 (기본값: `true`).

## 참고
Cartographer에 대한 자세한 정보는 [Cartographer 공식 문서](https://google-cartographer-ros.readthedocs.io/)를 참조하세요.