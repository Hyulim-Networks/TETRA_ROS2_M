# tetra_interface

## 설명
`tetra_interface` 패키지는 Tetra 로봇의 RS232 기반 인터페이스를 제공하며, 전원 모듈, 범퍼, 초음파 센서 및 기타 하드웨어 장치와의 통신을 지원합니다. 이 패키지는 ROS2 노드와 서비스를 통해 하드웨어 제어 및 상태 정보를 제공합니다.

## 의존성
- ament_cmake
- rclcpp
- rmw_implementation
- std_msgs
- std_srvs
- sensor_msgs
- geometry_msgs
- PCL
- interfaces (사용자 정의 메시지 및 서비스 패키지)

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `tetra_interface` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select tetra_interface
   ```

## 주요 파일 설명
### include/
- **`rs232.h`**: RS232 포트 열기, 닫기 및 터미널 설정 관련 함수 정의.
- **`rs232_common.h`**: RS232 통신 프로토콜 및 유틸리티 함수 정의.

### src/
- **`tetra_interface.cpp`**: ROS2 노드의 메인 파일로, 하드웨어 제어 및 상태 정보를 처리합니다.
- **`power_module.c`**: 전원 모듈 제어 및 데이터 읽기 기능 구현.
- **`dssp_rs232_power_module.c`**: RS232 기반 전원 모듈 통신 구현.

### launch/
- **`tetra_interface.launch.py`**: ROS2 노드를 실행하는 Python 형식의 launch 파일.
- **`tetra_interface_launch.xml`**: XML 형식의 launch 파일.

## 주요 노드 및 서비스
### 노드
- **`tetra_interface`**: RS232 기반 하드웨어와 통신하며, 센서 데이터 및 제어 명령을 처리합니다.

## 주요 서비스
### 기본 서비스
- **`/led_cmd`**: LED를 제어합니다.
- **`/led_toggle_cmd`**: LED의 토글 상태를 제어합니다.
- **`/turn_on_cmd`**: 특정 장치를 활성화합니다.
- **`/log_cmd`**: 통합 로그 데이터를 처리합니다.
- **`/Power_set_outport_cmd`**: 출력 포트를 설정합니다.
- **`/Power_get_io_status_cmd`**: IO 상태를 읽습니다.
- **`/Power_set_enable_cmd`**: 출력 포트를 활성화합니다.
- **`/Power_set_single_outport_cmd`**: 단일 출력 포트를 설정합니다.
- **`/Power_set_single_enable_cmd`**: 단일 출력 포트를 활성화합니다.
- **`/Power_wheel_enable_cmd`**: 휠을 활성화합니다.
- **`/Power_parameter_read_cmd`**: 파라미터를 읽습니다.
- **`/Power_parameter_write_cmd`**: 파라미터를 설정합니다.
- **`/Power_data_read_cmd`**: 전원 데이터를 읽습니다.
- **`/Power_adc_read_cmd`**: ADC 데이터를 읽습니다.
- **`/Power_version_read_cmd`**: 전원 모듈의 버전을 읽습니다.

### 초음파(Ultrasonic) 옵션 서비스
- **`/Power_sonar_read_cmd`**: 초음파 데이터를 읽습니다.
- **`/Power_sonar_cmd`**: 초음파 명령을 설정합니다.

### 컨베이어(Conveyor) 옵션 서비스
- **`/Conveyor_parameter_read_cmd`**: 컨베이어 파라미터를 읽습니다.
- **`/Conveyor_auto_move_cmd`**: 컨베이어의 자동 이동을 제어합니다.
- **`/Conveyor_manual_movement_cmd`**: 컨베이어의 수동 이동을 제어합니다.
- **`/Conveyor_parameter_write_cmd`**: 컨베이어 파라미터를 설정합니다.
- **`/Conveyor_data_read_cmd`**: 컨베이어 데이터를 읽습니다.

## 추가 옵션
### 초음파(Ultrasonic) 옵션
- 초음파 센서를 통해 최대 8개의 거리 데이터를 수집할 수 있습니다.
- 초음파 데이터는 `sensor_msgs/msg/Range` 메시지 형식으로 퍼블리시되거나 PointCloud2 데이터로 변환될 수 있습니다.

### 컨베이어(Conveyor) 옵션
- 컨베이어 센서 상태와 이동 상태를 퍼블리시합니다.
- 자동 및 수동 이동 모드를 지원합니다.

## 사용 방법
1. Launch 파일 실행:
   ```bash
   ros2 launch tetra_interface tetra_interface.launch.py
   ```
2. 서비스 호출 예시:
   ```bash
   ros2 service call /Power_outport_cmd interfaces/srv/PowerSetOutport "{id: 1, value: 100}"
   ```
3. 초음파 데이터를 읽으려면:
   ```bash
   ros2 service call /Power_sonar_read_cmd interfaces/srv/PowerSonarRead "{}"
   ```
4. 컨베이어를 수동으로 이동하려면:
   ```bash
   ros2 service call /Conveyor_manual_move_cmd interfaces/srv/ConveyorManualMovement "{direction: 'forward', speed: 50}"
   ```

## 참고
RS232 통신 및 ROS2 서비스에 대한 자세한 정보는 [ROS2 공식 문서](https://docs.ros.org/en/foxy/)를 참조하세요.