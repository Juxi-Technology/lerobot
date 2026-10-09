English | [简体中文](../zh-hans/urdf-and-resources.md) | [繁體中文](../zh-hant/urdf-and-resources.md) | [Deutsch](../de/urdf-and-resources.md) | [Español](../es/urdf-and-resources.md) | [Français](../fr/urdf-and-resources.md) | [Italiano](../it/urdf-and-resources.md) | [日本語](../ja/urdf-and-resources.md) | [한국어](../ko/urdf-and-resources.md) | [Português (BR)](../pt-br/urdf-and-resources.md) | [Português (PT)](../pt-pt/urdf-and-resources.md)

<title>URDF Files and Reference Resources</title>

# Lerbot's official [URDF file](https://github.com/TheRobotStudio/SO-ARM100/blob/main/Simulation/SO101/so101_new_calib.urdf)



## URDF Studio

https://urdf.d-robotics.cc/



## ROS2 simulation control (implement it yourself)

https://github.com/holmsslk/so-arm-moveit-hardware



## LeRobot's official graphical interface

https://github.com/huggingface/leLab

LeLab is a web app that brings all of LeRobot's workflow — calibration, teleoperation, recording, training, playback — into a single browser interface. Just connect the robotic arm, open the app, and you can start working. No cumbersome command-line work and no keyboard input required.

🤗 LeRobot's native web entry point, designed to let new users go from "out of the box" to "training their first policy" in a matter of minutes.

🤗 Install and run everything with a single command.



# Controlling the Follower Arm from a Phone

https://huggingface.co/docs/lerobot/main/en/phone_teleop



## Cloud robotics development: ROS 2 devices and Isaac Sim LeRobot simulation and data streaming on AWS

https://github.com/ti/ti.github.io/blob/95261efa4f8bdb4c8571920762318a532e58c7fd/%E5%BC%80%E5%8F%91/isaac/aws-ros2-isaac.md



## Setting servo IDs and center calibration in the web UI

https://bambot.org/feetech.js?lang=zh

1. Enter 0 or 1 depending on the servo model, then click "Connect"

![The image shows the connection interface for setting servo IDs and center calibration in the web UI. The interface has a "Connect" section containing a baud-rate dropdown, currently set to "1,000,000 bps (Index 0)"; a protocol-end dropdown, currently set to "0=STS/SMS"; and a "Connect" button. The bottom of the interface shows "Status: Disconnected". The image is closely tied to the context: after entering 0 or 1 depending on the servo model and clicking "Connect", servos with IDs 1~6 are scanned to confirm the corresponding ID servo — this is a key interface in that flow.](../en/images/d68-01.png)

2. Scan servos with IDs 1\~6; use FOUND in the scan results to confirm the corresponding ID servo. For example, in the image servo ID 1 was found

![The image shows the servo-scanning interface in Lerbot's official URDF Studio. The interface shows a start ID of 1 and an end ID of 6, with a "Start scan" button below. In the scan results, scanning ID1 found ID1239, while scanning ID2 through ID6 each reports "ERROR: Exception reading position from servo 2: \[TxRxResult\] There is no status packet!, Error code: 0". This image relates to the servo-scanning operation in Lerbot's official URDF Studio described in the context and visually presents the scan process and its results.](../en/images/fix-01.png)

3. ID setting and center calibration

① Set the current servo ID input to the scanned servo's ID

② Enter a number in "ID management" and click "Change ID" to set the ID

③ Center calibration (the STS3215 servo center is 2047, the SCS0009 servo center is 511)

STS servo: enter 2047 in "Position control" and click "Set"

SCS servo: enter 511 in "Position control" and click "Set"

![The image shows Lerbot's single-servo control interface. The "Current servo ID" is shown as 1; below, under "ID management," there is the number 1 and a "Change ID" button, with the message "Success: ID changed to 1" below. In the Position Control area there is a "Read position" button showing position 2047, next to a "Set" button. This image relates to the "ID setting and center calibration" section of the document and visually presents the interface for setting servo IDs and calibrating the center, helping users understand how to perform these settings in Lerbot.](../en/images/d68-02.png)
