English | [简体中文](../zh-hans/ros2-simulation.md) | [繁體中文](../zh-hant/ros2-simulation.md) | [Deutsch](../de/ros2-simulation.md) | [Español](../es/ros2-simulation.md) | [Français](../fr/ros2-simulation.md) | [Italiano](../it/ros2-simulation.md) | [日本語](../ja/ros2-simulation.md) | [한국어](../ko/ros2-simulation.md) | [Português (BR)](../pt-br/ros2-simulation.md) | [Português (PT)](../pt-pt/ros2-simulation.md)

# ROS2 Simulation Control

<figure view-type="Card">[Attachment: SO-ARM101_ROS2.zip](../en/images/SO-ARM101_ROS2.zip)</figure>

A complete ROS 2 workspace for the SO-ARM101 6-DOF robotic arm, covering the robot description, a built-in hardware driver, Gazebo simulation and MoveIt 2 motion planning.

The SO-ARM101 is the second-generation open-source follower arm co-designed by [TheRobotStudio](https://www.therobotstudio.com/) and the [LeRobot](https://huggingface.co/lerobot) community, using six STS3215 servos, a servo driver board and 3D-printed PLA+ parts.

<callout emoji="📌">
**Note: the arm requires center calibration; perform center calibration while all joints are in the middle of their range of motion**
</callout>

## Package Structure

<sheet sheet-id="wvspXe" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

Target platform: **ROS 2 Humble / Jazzy**.

---

## Preparing the ROS 2 Environment

Before building this project, make sure ROS 2 and the relevant components are installed on your system.

### System Requirements

- Ubuntu 22.04 (recommended) or 24.04
- At least 4 GB of RAM
- A USB serial port is required for real-hardware mode

### 0.1  Install ROS 2 Humble

```Bash
# Set locale
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

# Add the ROS 2 software repository
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Install ROS 2 Humble Desktop
sudo apt update
sudo apt install ros-humble-desktop
```

### 0.2  Install Build Tools and Dependencies

```Bash
# colcon build tool
sudo apt install python3-colcon-common-extensions

# MoveIt 2
sudo apt install ros-humble-moveit

# ros2_control
sudo apt install ros-humble-ros2-control \
                 ros-humble-ros2-controllers \
                 ros-humble-controller-manager \
                 ros-humble-joint-state-publisher-gui
```

### 0.3  Set Environment Variables

```Bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### 0.4  Set Serial Port Permissions (required for real hardware)

**Permanent setup (recommended)**:

```Bash
sudo usermod -a -G dialout $USER
# Takes effect after you log out and back in
```

**Temporary setup (must be redone after each reboot)**:

```Bash
sudo chmod 666 /dev/ttyACM0
```

## Installing the Workspace

```Markdown
# Step 1  Create the workspace
mkdir -p ~/so101_ws/src
cd ~/so101_ws/src

# Step 2  Put the source code in
cp -r /path/to/SO-ARM101_ROS2 ./

# Step 3  Install system dependencies
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y

# Step 4  Build all packages
colcon build --symlink-install

# Step 5  Load the environment  ← run this in every new terminal
source install/setup.bash
```

<callout emoji="💡">
**Real-hardware note** — the `so_arm_hardware` package is built in. No extra driver needs to be installed;  
it talks directly to the STS3215 servos over the serial port using the SCS protocol.
</callout>

## Visual Verification

Start here — it is the simplest path: no controllers, no hardware.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description view_description.launch.py rviz:=true
```

RViz displays the full robot model; drag the sliders to verify that each joint moves correctly.

---

## Controller Test (virtual hardware / Mock mode)

Still no real robot needed — everything runs in memory.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py
```

When the log shows the following, it is ready:

```Bash
joint_state_broadcaster      → active
joint_trajectory_controller  → active
```

<callout emoji="💡">
**Note**: simulation mode starts only two controllers (`joint_state_broadcaster` and  
`joint_trajectory_controller`). `gripper_controller` has been removed; the gripper  
is controlled together with all 6 joints by `joint_trajectory_controller`.
</callout>

### Controller Responsibilities

<sheet sheet-id="nGp7wf" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

## MoveIt Motion Planning (Mock hardware)

**Only one terminal needed** — MoveIt starts the controller stack internally.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py
```

Once the RViz window opens:

1. In the **MotionPlanning** panel, set **Planning Group → manipulator**
2. **Start State → `<current>`**, **Goal State → extended**
3. Click **Plan** and then **Execute**

Available preset poses: `open`, `zero`, `extended`, `rest`.

### 4.1  MoveIt Interface Walkthrough

After RViz starts, the **MotionPlanning** panel appears on the left with the following main tabs:

#### Planning Tab

<sheet sheet-id="MAE5MJ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

#### Planning Parameters

<sheet sheet-id="D0Q6xA" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

> **First-test tip**: set Velocity and Acceleration to 0.3 to slow the motion for safety.

#### Scene Objects Tab

- Add obstacles (Box / Sphere / Cylinder) for collision checking
- Import / export scenes
- MoveIt automatically plans around obstacles

#### Stored States Tab

- Save frequently used arm poses
- Default poses: `open`, `zero`, `extended`, `rest`

### 4.2  Basic Workflow

#### Method A: Interactive dragging (recommended)

1. In the 3D view, find the **interactive marker** at the end of the arm (colored arrows and rings)
2. Drag the arrows to translate the end-effector position, and drag the rings to rotate the orientation
3. The system solves IK automatically and updates the joint angles in real time
4. Click **Plan** to view the planned trajectory (orange)
5. Once satisfied, click **Execute** to run it

> If dragging stutters, start from the `rest` preset pose before dragging.

#### Method B: Preset poses

1. **Query Goal State** dropdown → select `open` / `extended` / `rest`, etc.
2. Click **Update**
3. Click **Plan**
4. Click **Execute**

#### Method C: Setting joint angles manually

1. **Query Goal State** → **Joints** tab
2. Drag each joint slider to set the target angle
3. Joint range reference:

<sheet sheet-id="nmKRig" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

1. Click **Update**
2. Click **Plan**
3. Click **Execute**

#### Method D: Random valid target

Click **Random Valid** to generate a random reachable pose, then Plan → Execute.

### 4.3  Safety Notes

1. **Slow down on first use**: set Velocity / Acceleration to 0.1–0.3
2. **Emergency stop**: press Ctrl+C at any time to terminate the program, or cut the power
3. **Joint limits**: MoveIt will not plan beyond the ranges in `joint_limits.yaml`, but make sure those are configured correctly
4. **Real hardware**: make sure there is enough space around the arm before executing

### MoveIt Configuration Overview

<sheet sheet-id="Vvlwrc" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Gazebo Simulation

Gazebo simulation requires **4 terminals running at the same time**. Follow the order strictly.

### 5.1  Start Gazebo simulation  (Terminal 1)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py
```

Wait for the Gazebo window to appear; the robot hangs briefly in the air and then lands.

### 5.2  Load the trajectory controller  (Terminal 2)

By default Gazebo activates only `forward_position_controller`; you must manually switch to  
`joint_trajectory_controller`:

```Markdown
#  Terminal 2
source ~/so101_ws/install/setup.bash

# Step A — turn off forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# Step B — load and activate joint_trajectory_controller with the spawner
ros2 run controller_manager spawner joint_trajectory_controller

# Step C — verify
ros2 control list_controllers
```

Expected output:

```Bash
forward_position_controller  inactive
joint_state_broadcaster      active
joint_trajectory_controller  active
```

<callout emoji="💡">
⚠️ Do not use `ros2 control load_controller` first! It puts the controller into the  
`unconfigured` state, which prevents the spawner from activating it. If you already did,  
run `unload_controller` first and start over.
</callout>

### 5.3  Start move_group  (Terminal 3)

```Bash
#  Terminal 3
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py use_sim_time:=True
```

### 5.4  Start RViz  (Terminal 4)

```Bash
#  Terminal 4
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

Once RViz is ready:

1. **Planning Group → manipulator**
2. **Goal State → open** (or `extended`, `rest`)
3. Click **Plan** and then **Execute**

The arm joints in Gazebo will follow the motion.

<callout emoji="💡">
**Note**: because of the PID gain limitation in the Humble version of `gz_ros2_control`,  
the gripper may not physically open in Gazebo (the execution log still reports success).  
Mock mode and real hardware do not have this problem.
</callout>

### 5.5  Headless mode (no GUI)

```Bash
ros2 launch so_arm_gz so_arm_gz_bringup.launch.py \
  gazebo_gui:=false \
  launch_rviz:=false
```

### 5.6  Troubleshooting: repeated load failures

If the spawner keeps reporting `Failed to activate controller`, do the following to fully reset:

```Bash
# 1. Unload the stuck controller
ros2 control unload_controller joint_trajectory_controller

# 2. Turn off forward_position_controller
ros2 control set_controller_state forward_position_controller inactive

# 3. Spawn again
ros2 run controller_manager spawner joint_trajectory_controller
```

## Real Hardware

Prerequisite: the SO-ARM101 arm is assembled and the servo driver board is connected to the PC via USB.

### 6.1  Start the controllers (optional)

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_description controllers_bringup.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

The `so_arm_hardware` plugin automatically:

1. Opens the serial port
2. Scans the 6 servo IDs (1–6)
3. Verifies that every servo responds
4. Enables torque and reads the current position

Once the controllers are ready, open two more terminals to start MoveIt:

```Bash
#  Terminal 2 — move_group
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config move_group.launch.py
```

```Bash
#  Terminal 3 — RViz
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config moveit_rviz.launch.py
```

### 6.2  MoveIt (one-command startup)

> The following command **replaces** 6.1 (do not run both at the same time; stop the 6.1 commands) — `demo.launch.py` already includes the controller stack internally.

```Bash
#  Terminal 1
source ~/so101_ws/install/setup.bash
ros2 launch so_arm101_moveit_config demo.launch.py \
  hardware_type:=real \
  usb_port:=/dev/ttyACM0
```

### 6.3  Serial Port Troubleshooting

<sheet sheet-id="HadQEu" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### 6.4  RViz Display Does Not Match the Actual Pose

If the arm pose in RViz does not match the real hardware (for example a joint offset or a false collision report):

1. Confirm the servos have been center-calibrated
2. Adjust the `position_offset` of each joint in `so_arm101.ros2_control.xacro`
3. Conversion formula: `new offset = current offset + (currently displayed rad / 0.00153398)`
4. Rebuild the `so_arm101_description` package after the change

---

## FAQ

### Q1: "package not found" when building

**A**: Make sure all system dependencies are installed correctly and the ROS 2 environment is sourced:

```Bash
source /opt/ros/humble/setup.bash
cd ~/so101_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

### Q2: "Permission denied" accessing the serial port at startup

**A**: Check the serial port permissions:

```Bash
# Temporary fix
sudo chmod 666 /dev/ttyACM0

# Permanent fix (takes effect after logout)
sudo usermod -a -G dialout $USER
```

### Q3: MoveIt planning fails with "Motion planning start tree could not be initialized"

**A**: There are usually two causes:

1. **Joints out of bounds** — check the `FixStartStateBounds` output in the log. The current tolerance is  
0.3 rad; if the overshoot is within that range it passes. Otherwise adjust `start_state_max_bounds_error`  
or check the servo offsets.
2. **Start state in collision** — check the `FixStartStateCollision` output in the log. If  
"Unable to find a valid state nearby" appears, the current pose is self-colliding.  
The arm may be in a folded pose (for example the gripper touching the shoulder), or the offsets are incorrect.  
Adjust `position_offset` and try again.

### Q4: The arm does not move after Execute

**A**: Check the controller states:

```Bash
ros2 control list_controllers
```

Make sure `joint_trajectory_controller` is `active`. If not, spawn it again:

```Bash
ros2 run controller_manager spawner joint_trajectory_controller
```

### Q5: RViz starts slowly or hangs

**A**: This is normal. On startup MoveIt loads the URDF model, collision-checking plugins,  
kinematics solvers and so on; the first launch takes about 10 seconds.

### Q6: The planned path is not smooth or is jerky

**A**: Try the following:

- Switch to a different planner (choose `RRTConnect` from the Planner dropdown in RViz)
- Increase Planning Time to 10 seconds
- Make sure the target is inside the workspace (test with `Random Valid`)

### Q7: The gripper does not move in Gazebo

**A**: This is a hard-coded PID gain limitation in the Humble version of `gz_ros2_control`  
(fixed at 0.1) that cannot be overridden via URDF parameters. Execute reports success in the log,  
but the gripper does not open in Gazebo's physics simulation. Mock mode and real hardware do not have this problem.

## Appendix: Launch Parameter Quick Reference

### `controllers_bringup.launch.py`

<sheet sheet-id="z9iTwQ" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

### `so_arm_gz_bringup.launch.py`

<sheet sheet-id="6UXvuS" token="Xi7PsUuX5hut2Zt5VXWcaGFUnce"></sheet>

---

## Directory Layout

```Bash
SO-ARM101_ROS2/
├── so_arm_utils/                   # Python utility library
├── so_arm101_description/          # URDF · controllers · meshes · RViz · MuJoCo
├── so_arm101_moveit_config/        # MoveIt 2 SRDF · planners · launch files
├── so_arm_gz/                      # Gazebo simulation launch
├── so_arm_hardware/                # Built-in SCS serial driver (C++)
└── Simulation/                     # Original CAD URDF (kept for reference)
```
