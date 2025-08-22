# 🧩 Interfaces

## 📖 개요
Interfaces 패키지는 ROS2 메시지와 서비스를 정의합니다. 이 패키지는 Tetra 로봇의 다양한 기능을 지원하기 위한 인터페이스를 제공합니다.

## 📂 주요 파일
- 📂 `msg/`: ROS2 메시지 정의.
- 📂 `srv/`: ROS2 서비스 정의.

## 🛠️ 사용 방법
1. 메시지 및 서비스 정의를 사용하여 ROS2 노드 개발.

## 설명
ROS2 메시지 및 서비스 인터페이스를 정의하는 패키지입니다. 이 패키지는 Tetra 로봇의 다양한 기능을 제어하고 데이터를 교환하기 위한 메시지와 서비스를 제공합니다.

## 의존성
- ament_cmake
- builtin_interfaces
- std_msgs
- std_srvs
- geometry_msgs

## 설치 방법
1. ROS2 워크스페이스를 설정합니다.
2. `interfaces` 디렉토리를 `src` 폴더에 복사합니다.
3. 워크스페이스 루트에서 다음 명령어를 실행합니다:
   ```bash
   colcon build --packages-select interfaces
   ```

## 메시지 및 서비스 리스트
### 메시지
- **`Gpio.msg`**: GPIO 입력 및 출력 상태를 나타내는 메시지.

### 서비스
- **`AngularPositionMove.srv`**: 각도 위치 이동 명령.
- **`ConveyorAutoMovement.srv`**: 컨베이어 자동 이동 제어.
- **`ConveyorDataRead.srv`**: 컨베이어 시스템 데이터 읽기.
- **`ConveyorManualMovement.srv`**: 컨베이어 수동 이동 제어.
- **`ConveyorParameterRead.srv`**: 컨베이어 매개변수 읽기.
- **`ConveyorParameterWrite.srv`**: 컨베이어 매개변수 쓰기.
- **`DeleteMap.srv`**: 맵 삭제 명령.
- **`DockingControl.srv`**: 도킹 제어 명령.
- **`DockingStop.srv`**: 도킹 중지 명령.
- **`GetInformation.srv`**: 로봇 상태 정보 가져오기.
- **`GotoCancel.srv`**: 이동 취소 명령.
- **`GotoLocation.srv`**: 특정 위치로 이동 명령.
- **`GotoLocation2.srv`**: 좌표 기반 이동 명령.
- **`ImuReset.srv`**: IMU 오일러 각도 초기화.
- **`Integrallog.srv`**: 적분 로그 명령.
- **`LedControl.srv`**: LED 제어 명령.
- **`LedToggleControl.srv`**: LED 토글 제어 명령.
- **`LinearPositionMove.srv`**: 선형 위치 이동 명령.
- **`ParameterRead.srv`**: 매개변수 읽기 명령.
- **`ParameterWrite.srv`**: 매개변수 쓰기 명령.
- **`PowerAdcRead.srv`**: 전력 센서 ADC 데이터 읽기.
- **`PowerDataRead.srv`**: 전력 센서 시스템 데이터 읽기.
- **`PowerGetIoStatus.srv`**: IO 상태 확인.
- **`PowerParameterRead.srv`**: 전력 센서 매개변수 읽기.
- **`PowerParameterWrite.srv`**: 전력 센서 매개변수 쓰기.
- **`PowerSetEnable.srv`**: 전원 On/Off 제어.
- **`PowerSetOutport.srv`**: GPIO 출력 On/Off 제어.
- **`PowerSetSingleEnable.srv`**: 단일 출력 제어.
- **`PowerSetSingleOutport.srv`**: 단일 GPIO 출력 제어.
- **`PowerSonarCmd.srv`**: 소나 시작/중지 명령.
- **`PowerSonarRead.srv`**: 소나 데이터 읽기.
- **`PowerVersionRead.srv`**: 전력 센서 버전 데이터 읽기.
- **`PowerWheelEnable.srv`**: 휠 전원 On/Off 제어.
- **`RunCollisionMonitor.srv`**: 충돌 모니터 실행.
- **`RunMapping.srv`**: 맵핑 실행.
- **`RunNavigation.srv`**: 내비게이션 실행.
- **`SaveMaker.srv`**: 마커 저장 명령.
- **`SaveMap.srv`**: 맵 저장 명령.
- **`Servo.srv`**: 서보 모터 On/Off 제어.
- **`SetLocation.srv`**: 위치 설정 명령.
- **`SetMaxspeed.srv`**: 최대 속도 제한 설정.
- **`SetMoveMode.srv`**: 이동 모드 설정.
- **`ToggleOn.srv`**: LED 토글 On 제어.

## 사용 방법 예시
1. 메시지 및 서비스를 빌드합니다:
   ```bash
   colcon build --packages-select interfaces
   ```
2. 다른 패키지에서 인터페이스를 사용하여 Tetra 로봇의 기능을 제어합니다.