[English](../en/ros2-simulation.md) | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | 한국어 | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# ROS2 시뮬레이션 제어

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

SO-ARM101 6-DOF 로봇 팔을 위한 완전한 ROS 2 워크스페이스로, 로봇 설명, 내장 하드웨어 드라이버, Gazebo 시뮬레이션, MoveIt 2 모션 플래닝을 다룹니다.

SO-ARM101은 [TheRobotStudio](https://www.therobotstudio.com/)와 [LeRobot](https://huggingface.co/lerobot) 커뮤니티가 공동 설계한 2세대 오픈소스 Follower 암으로, 6개의 STS3215 서보, 서보 드라이버 보드, 3D 프린팅 PLA+ 부품을 사용합니다.

<callout emoji="📌">
**참고: 이 팔은 중심 캘리브레이션이 필요합니다. 모든 관절이 가동 범위의 중간에 있는 상태에서 중심 캘리브레이션을 수행하십시오**
</callout>

## 패키지 구성

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

대상 플랫폼: **ROS 2 Humble / Jazzy**.

---

## ROS 2 환경 준비

이 프로젝트를 빌드하기 전에 시스템에 ROS 2와 관련 구성 요소가 설치되어 있는지 확인하십시오.

### 시스템 요구 사항

- Ubuntu 22.04 (권장) 또는 24.04
- 최소 4 GB RAM
- 실제 하드웨어 모드에는 USB 시리얼 포트가 필요합니다

### 0.1  ROS 2 Humble 설치

```Bash
# 로케일 설정
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# ROS 2 소프트웨어 저장소 추가
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# ROS 2 Humble Desktop 설치
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  빌드 도구 및 의존성 설치

```Bash
# colcon 빌드 도구
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  환경 변수 설정

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  시리얼 포트 권한 설정 (실제 하드웨어에 필요)

**영구 설정 (권장)**:

```Bash
sudo usermod -a -G dialout $USER
# 로그아웃 후 다시 로그인하면 적용됩니다
```

**임시 설정 (재부팅할 때마다 다시 해야 함)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## 워크스페이스 설치

```Markdown
# Step 1  워크스페이스 생성
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Step 2  소스 코드 배치
cp -r /path/to/SO-ARM101_ROS2 ./

# Step 3  시스템 의존성 설치
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Step 4  모든 패키지 빌드
colcon build --symlink-install

# Step 5  환경 로드  ← 새 터미널마다 실행합니다
source install/setup.bash
```

<callout emoji="💡">
**실제 하드웨어 참고** — `so_arm_hardware` 패키지가 내장되어 있습니다. 추가 드라이버를 설치할 필요가 없으며,  
SCS 프로토콜을 사용해 시리얼 포트로 STS3215 서보와 직접 통신합니다.
</callout>

## 시각적 검증

여기서 시작하십시오. 컨트롤러도, 하드웨어도 필요 없는 가장 간단한 경로입니다.

```Bash
#  터미널 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz에 전체 로봇 모델이 표시됩니다. 슬라이더를 끌어 각 관절이 올바르게 움직이는지 확인하십시오.

---

## 컨트롤러 테스트 (가상 하드웨어 / Mock 모드)

여전히 실제 로봇은 필요 없습니다. 모든 것이 메모리에서 실행됩니다.

```Bash
#  터미널 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

로그에 다음이 표시되면 준비된 것입니다:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**참고**: 시뮬레이션 모드에서는 두 개의 컨트롤러 (`joint_state_broadcaster`와  
`joint_trajectory_controller`)만 시작됩니다. `gripper_controller`는 제거되었으며, 그리퍼는  
`joint_trajectory_controller`가 6개 관절 전체와 함께 제어합니다.
</callout>

### 컨트롤러 역할

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## MoveIt 모션 플래닝 (Mock 하드웨어)

**터미널 하나만 필요합니다** — MoveIt이 내부적으로 컨트롤러 스택을 시작합니다.

```Bash
#  터미널 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

RViz 창이 열리면:

1. **MotionPlanning** 패널에서 **Planning Group → manipulator**를 설정합니다
2. **Start State → `<current>`**, **Goal State → extended**
3. **Plan**을 클릭한 다음 **Execute**를 클릭합니다

사용 가능한 사전 설정 자세: `open`, `zero`, `extended`, `rest`.

### 4.1  MoveIt 인터페이스 살펴보기

RViz가 시작되면 왼쪽에 **MotionPlanning** 패널이 나타나며 다음 주요 탭이 있습니다:

#### Planning 탭

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Planning 파라미터

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **첫 테스트 팁**: 안전을 위해 Velocity와 Acceleration을 0.3으로 설정해 동작을 느리게 하십시오.

#### Scene Objects 탭

- 충돌 검사를 위한 장애물 (Box / Sphere / Cylinder) 추가
- 씬 가져오기 / 내보내기
- MoveIt이 장애물을 우회해 자동으로 플래닝합니다

#### Stored States 탭

- 자주 쓰는 팔 자세 저장
- 기본 자세: `open`, `zero`, `extended`, `rest`

### 4.2  기본 워크플로

#### 방법 A: 대화형 드래그 (권장)

1. 3D 뷰에서 팔 끝의 **대화형 마커** (색색의 화살표와 링)를 찾습니다
2. 화살표를 끌어 엔드이펙터 위치를 이동하고, 링을 끌어 방향을 회전시킵니다
3. 시스템이 IK를 자동으로 풀고 관절 각도를 실시간으로 갱신합니다
4. **Plan**을 클릭해 계획된 궤적 (주황색)을 확인합니다
5. 만족하면 **Execute**를 클릭해 실행합니다

> 드래그가 끊기면 `rest` 사전 설정 자세에서 시작한 뒤 드래그하십시오.

#### 방법 B: 사전 설정 자세

1. **Query Goal State** 드롭다운 → `open` / `extended` / `rest` 등을 선택합니다
2. **Update**를 클릭합니다
3. **Plan**을 클릭합니다
4. **Execute**를 클릭합니다

#### 방법 C: 관절 각도 수동 설정

1. **Query Goal State** → **Joints** 탭
2. 각 관절 슬라이더를 끌어 목표 각도를 설정합니다
3. 관절 범위 참고:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. **Update**를 클릭합니다
2. **Plan**을 클릭합니다
3. **Execute**를 클릭합니다

#### 방법 D: 임의의 유효 목표

**Random Valid**를 클릭해 임의의 도달 가능한 자세를 생성한 뒤 Plan → Execute를 수행합니다.

### 4.3  안전 참고 사항

1. **처음 사용 시 속도를 낮추십시오**: Velocity / Acceleration을 0.1–0.3으로 설정합니다
2. **비상 정지**: 언제든 Ctrl+C를 눌러 프로그램을 종료하거나 전원을 차단합니다
3. **관절 한계**: MoveIt은 `joint_limits.yaml`의 범위를 넘어 플래닝하지 않지만, 이 값이 올바르게 설정되어 있는지 확인하십시오
4. **실제 하드웨어**: 실행 전에 팔 주변에 충분한 공간이 있는지 확인하십시오

### MoveIt 구성 개요

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Gazebo 시뮬레이션

Gazebo 시뮬레이션은 **4개의 터미널을 동시에 실행**해야 합니다. 순서를 엄격히 지키십시오.

### 5.1  Gazebo 시뮬레이션 시작  (터미널 1)

```Bash
#  터미널 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Gazebo 창이 나타날 때까지 기다리십시오. 로봇이 잠시 공중에 떠 있다가 착지합니다.

### 5.2  궤적 컨트롤러 로드  (터미널 2)

기본적으로 Gazebo는 `forward_position_controller`만 활성화하므로, 수동으로  
`joint_trajectory_controller`로 전환해야 합니다:

```Markdown
#  터미널 2
source ~/so101_ws/install/setup.bash

# Step A — forward_position_controller 끄기
ros2 control set_controller_state forward_position_controller inactive

# Step B — spawner로 joint_trajectory_controller 로드 및 활성화
ros2 run controller_manager spawner joint_trajectory_controller

# Step C — 확인
ros2 control list_controllers
```

예상 출력:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ 먼저 `ros2 control load_controller`를 사용하지 마십시오! 이 명령은 컨트롤러를  
`unconfigured` 상태로 만들어 spawner가 활성화하지 못하게 합니다. 이미 실행했다면  
`unload_controller`를 먼저 실행하고 다시 시작하십시오.
</callout>

### 5.3  move_group 시작  (터미널 3)

```Bash
#  터미널 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  RViz 시작  (터미널 4)

```Bash
#  터미널 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

RViz가 준비되면:

1. **Planning Group → manipulator**
2. **Goal State → open** (또는 `extended`, `rest`)
3. **Plan**을 클릭한 다음 **Execute**를 클릭합니다

Gazebo의 팔 관절이 그 동작을 따라갑니다.

<callout emoji="💡">
**참고**: `gz_ros2_control`의 Humble 버전에서 PID 게인 제한 때문에  
그리퍼가 Gazebo에서 물리적으로 열리지 않을 수 있습니다 (실행 로그는 여전히 성공으로 보고합니다).  
Mock 모드와 실제 하드웨어에는 이 문제가 없습니다.
</callout>

### 5.5  헤드리스 모드 (GUI 없음)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  문제 해결: 반복적인 로드 실패

spawner가 `Failed to activate controller`를 계속 보고하면, 다음과 같이 완전히 초기화하십시오:

```Bash
# 1. 멈춘 컨트롤러 언로드
ros2 control unload_controller joint_trajectory_controller

# 2. forward_position_controller 끄기
ros2 control set_controller_state forward_position_controller inactive

# 3. 다시 spawn
ros2 run controller_manager spawner joint_trajectory_controller
```

## 실제 하드웨어

사전 조건: SO-ARM101 팔이 조립되어 있고 서보 드라이버 보드가 USB로 PC에 연결되어 있어야 합니다.

### 6.1  컨트롤러 시작 (선택 사항)

```Bash
#  터미널 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

`so_arm_hardware` 플러그인은 자동으로:

1. 시리얼 포트를 엽니다
2. 6개 서보 ID (1–6)를 스캔합니다
3. 모든 서보가 응답하는지 검증합니다
4. 토크를 활성화하고 현재 위치를 읽습니다

컨트롤러가 준비되면 터미널 두 개를 더 열어 MoveIt을 시작하십시오:

```Bash
#  터미널 2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  터미널 3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (원커맨드 시작)

> 다음 명령은 6.1을 **대체합니다** (동시에 둘 다 실행하지 마십시오. 6.1의 명령을 중지하십시오) — `demo.launch.py`는 내부에 컨트롤러 스택을 이미 포함하고 있습니다.

```Bash
#  터미널 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  시리얼 포트 문제 해결

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  RViz 표시가 실제 자세와 일치하지 않음

RViz의 팔 자세가 실제 하드웨어와 일치하지 않으면 (예: 관절 오프셋 또는 잘못된 충돌 보고):

1. 서보의 중심 캘리브레이션이 완료되었는지 확인합니다
2. `so_arm101.ros2_control.xacro`에서 각 관절의 `position_offset`을 조정합니다
3. 변환 공식: `new offset = current offset + (currently displayed rad / 0.00153398)`
4. 변경 후 `so_arm101_description` 패키지를 다시 빌드합니다

---

## FAQ

### Q1: 빌드 시 "package not found" 발생

**A**: 모든 시스템 의존성이 올바르게 설치되었고 ROS 2 환경이 소싱되었는지 확인하십시오:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### Q2: 시작 시 시리얼 포트 접근에서 "Permission denied" 발생

**A**: 시리얼 포트 권한을 확인하십시오:

```Bash
# 임시 해결
sudo chmod 666 /dev/ttyACM0

# 영구 해결 (로그아웃 후 적용)
sudo usermod -a -G dialout $USER
```

### Q3: MoveIt 플래닝이 "Motion planning start tree could not be initialized"로 실패

**A**: 보통 두 가지 원인이 있습니다:

1. **관절 범위 초과** — 로그에서 `FixStartStateBounds` 출력을 확인하십시오. 현재 허용 오차는  
0.3 rad이며, 초과분이 그 범위 안이면 통과합니다. 그렇지 않으면 `start_state_max_bounds_error`를 조정하거나  
서보 오프셋을 확인하십시오.
2. **시작 상태가 충돌 상태** — 로그에서 `FixStartStateCollision` 출력을 확인하십시오.  
"Unable to find a valid state nearby"가 나타나면 현재 자세가 자기 충돌 상태입니다.  
팔이 접힌 자세 (예: 그리퍼가 숄더에 닿음)이거나 오프셋이 잘못된 것일 수 있습니다.  
`position_offset`을 조정하고 다시 시도하십시오.

### Q4: Execute 후 팔이 움직이지 않음

**A**: 컨트롤러 상태를 확인하십시오:

```Bash
ros2 control list_controllers
```

`joint_trajectory_controller`가 `active`인지 확인하십시오. 그렇지 않으면 다시 spawn하십시오:

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### Q5: RViz가 느리게 시작되거나 멈춤

**A**: 정상입니다. 시작 시 MoveIt은 URDF 모델, 충돌 검사 플러그인,  
키네마틱스 솔버 등을 로드하므로 첫 실행에 약 10초가 걸립니다.

### Q6: 계획된 경로가 매끄럽지 않거나 덜컹거림

**A**: 다음을 시도하십시오:

- 다른 플래너로 전환합니다 (RViz의 Planner 드롭다운에서 `RRTConnect` 선택)
- Planning Time을 10초로 늘립니다
- 목표가 워크스페이스 안에 있는지 확인합니다 (`Random Valid`로 테스트)

### Q7: Gazebo에서 그리퍼가 움직이지 않음

**A**: 이는 `gz_ros2_control`의 Humble 버전에 하드코딩된 PID 게인 제한  
(0.1로 고정)으로, URDF 파라미터로 재정의할 수 없습니다. 로그에서 Execute는 성공으로 보고되지만,  
Gazebo의 물리 시뮬레이션에서 그리퍼가 열리지 않습니다. Mock 모드와 실제 하드웨어에는 이 문제가 없습니다.

## 부록: Launch 파라미터 빠른 참조

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## 디렉터리 레이아웃

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Python utility library
├── so_arm101_description/          # URDF · controllers · meshes · RViz · MuJoCo
├── so_arm101_moveit_config/        # MoveIt 2 SRDF · planners · launch files
├── so_arm_gz/                      # Gazebo simulation launch
├── so_arm_hardware/                # Built-in SCS serial driver (C++)
└── Simulation/                     # Original CAD URDF (kept for reference)
```
