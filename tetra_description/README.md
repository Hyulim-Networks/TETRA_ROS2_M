# tetra_description

## 설명
`tetra_description` 패키지는 Tetra 로봇의 URDF(Unified Robot Description Format) 파일과 관련 리소스를 제공합니다. 이 패키지는 로봇의 물리적 구조와 시각화를 정의하며, 시뮬레이션 및 실제 로봇의 상태를 퍼블리시하는 데 사용됩니다.

## 의존성
- ament_cmake
- xacro
- robot_state_publisher
- joint_state_publisher
- joint_state_publisher_gui

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `tetra_description` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select tetra_description
   ```

## 주요 파일 설명
### launch/
- **`tetra_description.launch.py`**: 로봇의 URDF를 로드하고 `robot_state_publisher`를 실행하는 launch 파일입니다.

### urdf/
- **`tetra.xacro`**: Tetra 로봇의 주요 URDF 파일로, 로봇의 구조와 링크를 정의합니다.
- **`base.urdf.xacro`**: 로봇의 기본 링크와 휠을 정의하는 파일입니다.
- **`materials.urdf.xacro`**: 로봇의 색상 및 재질을 정의하는 파일입니다.

### meshes/
- STL 파일들로, 로봇의 3D 모델을 정의합니다:
  - `caster_wheel.stl`
  - `caster_yoke.stl`
  - `platform_body.stl`
  - `wheel_drive_left.stl`
  - `wheel_drive_right.stl`

### rviz/
- **`rviz_basic_settings.rviz`**: RViz 설정 파일로, 로봇의 시각화를 위한 기본 설정을 포함합니다.

## 주요 노드
- **`robot_state_publisher`**: URDF를 로드하고 TF 트리를 퍼블리시합니다.
- **`joint_state_publisher`**: 로봇의 조인트 상태를 퍼블리시합니다.
- **`joint_state_publisher_gui`**: GUI를 통해 조인트 상태를 조작할 수 있습니다.

## 사용 방법
1. Launch 파일 실행:
   ```bash
   ros2 launch tetra_description tetra_description.launch.py
   ```
2. RViz에서 로봇 모델을 시각화하려면 `rviz/rviz_basic_settings.rviz` 파일을 로드합니다.

## 참고
URDF 및 Xacro 파일에 대한 자세한 정보는 [ROS2 공식 문서](https://docs.ros.org/en/foxy/Tutorials/URDF.html)를 참조하세요.