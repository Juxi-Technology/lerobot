English | [简体中文](../zh-hans/so-arm101-assembly.md) | [繁體中文](../zh-hant/so-arm101-assembly.md) | [Deutsch](../de/so-arm101-assembly.md) | [Español](../es/so-arm101-assembly.md) | [Français](../fr/so-arm101-assembly.md) | [Italiano](../it/so-arm101-assembly.md) | [日本語](../ja/so-arm101-assembly.md) | [한국어](../ko/so-arm101-assembly.md) | [Português (BR)](../pt-br/so-arm101-assembly.md) | [Português (PT)](../pt-pt/so-arm101-assembly.md)

<title>SO-ARM101 Robotic Arm Kit Assembly Tutorial</title>

<callout emoji="💡">
Note: skip this tutorial if you have a pre-assembled arm
</callout>

## 3D-printed parts for the follower arm

![This image shows the 3D-printed parts for the follower arm needed to assemble the SO-ARM101 robotic arm, all white PLA plastic parts arranged on a light wood-grain surface. The parts include connectors of various shapes, a forked structure with a grid, a base-type part with holes, a specially shaped forked support arm and so on, matching the tutorial's point that the follower arm's end is a gripper. These parts are the basic molded pieces for the follower arm of the arm and are the objects handled in the support-removal step, corresponding directly to the follower-arm 3D-printed parts introduced in the tutorial.](../en/images/d09-01.jpg)

## 3D-printed parts for the leader arm

![The image shows 3D-printed parts for the SO-ARM101 robotic arm. Various black 3D-printed parts are neatly arranged in the frame, with blue lines on the edges of some parts. These parts include structural pieces for the leader and follower arms, such as the gripper, handle and trigger, as well as connectors. The image corresponds to the "3D-printed parts for the leader arm" section of the document and visually presents the appearance of the 3D-printed parts, providing a reference for the later steps of removing leftover supports and telling the servos apart.](../en/images/d09-02.jpg)

The leader and follower arms are very similar; only the end differs

The leader has a handle and trigger; the follower has a gripper

## Removing leftover supports from the 3D-printed parts

Check every hole, opening, slot and grid, especially the five holes that resemble the "five dots" tile in mahjong

This step is very important; otherwise you will not be able to drive the screws in later

## Distinguishing the four servos

<table><colgroup><col/><col/><col/><col/><col/><col/></colgroup><tbody><tr><td vertical-align="middle">Large size</td><td vertical-align="middle">Small size</td><td vertical-align="middle">Voltage (V)</td><td vertical-align="middle">Gear ratio</td><td vertical-align="middle">Arm joint</td><td vertical-align="middle">Quantity</td></tr><tr><td rowspan="4" vertical-align="middle">STS-3215</td><td vertical-align="middle">C001</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:345</td><td vertical-align="middle">Leader 2</td><td vertical-align="middle">1</td></tr><tr><td vertical-align="middle">C044</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:191</td><td vertical-align="middle">Leader 1, 3</td><td vertical-align="middle">2</td></tr><tr><td vertical-align="middle">C046</td><td vertical-align="middle">7.4</td><td vertical-align="middle">1:147</td><td vertical-align="middle">Leader 4, 5, 6</td><td vertical-align="middle">3</td></tr><tr><td vertical-align="middle">C047</td><td vertical-align="middle">12</td><td vertical-align="middle">1:345</td><td vertical-align="middle">All follower joints</td><td vertical-align="middle">6</td></tr></tbody></table>

> The gear ratio is the ratio of "motor speed : servo output shaft speed"; for example, 1:345 means the motor turns 345 times for the output shaft to turn once.
> 
> A high gear ratio multiplies torque through the gear train, so it can drive a heavier load (such as the follower arm)
> 
> But at the same time, the output shaft turns more slowly (because it is "geared down")
> 
> Dragging the joint also takes more effort

Below are the models and gear ratios of all the servos in this project; the underlined parts are their numbers

![The image shows the servo models, voltages and gear ratios used in the arm. On the left is the leader arm, with two models, C046 (7.4V, 1:147) and C044 (7.4V, 1:191); on the right is the follower arm, with two models, C001 (7.4V, 1:345) and C047 (12V, 1:345). The image is closely tied to the context, which introduces the servo models, voltages and gear ratios of the leader and follower arms in detail; this image visually presents these key figures to help readers better understand the servo configuration.](../en/images/d09-03.png)

![The image shows four boxes of servos labeled "STS3215". Each box is printed with the word "SPECIFICATION" and includes parameters such as torque, speed and dimensions, for example a torque of 9.2kg·cm/127.98oz·in(6V). The STS3215-C001 has a torque of 12.5kg·cm/173.88oz·in(6V), and the STS3215-C046 has a torque of 16kg·cm/220.58oz·in(7V). These servos are the model used for all the joints of the arm's follower arm, corresponding to the follower arm introduced in the document, and are used for the servo installation in the later assembly steps.](../en/images/d09-04.jpg)

## Distinguishing the two power adapters

5V 6A 30W power adapter: powers the 7.4V servos (leader arm), black

12V 5A 60W power adapter, powers the 12V servos (follower arm), white

## Downloading the Feetech servo debugging tool

### Windows PC

https://gitee.com/ftservo/fddebug

Download [`FD1.9.8.5(250729).7z`](https://gitee.com/ftservo/fddebug/blob/master/FD1.9.8.5(250729).7z), extract it, and run the exe program inside

### Ubuntu and Mac (the archive includes a tutorial)

<figure view-type="Card">[Attachment: Juxi_ServoController.zip](../en/images/Juxi_ServoController.zip)</figure>

![This image is an auxiliary illustration for the SO-ARM101 robotic arm kit assembly tutorial, corresponding to the section on telling the power adapters apart. It shows two servo models and their mounting positions, STS3215-C001 and STS3215-C018, and also labels servos such as STS3215-C004, corresponding to the different joints of the arm. The figure also lists the parameters of these two servos, including rotation speed, stall torque, servo precision, protection features and parameter feedback, providing a reference for servo selection and installation during arm assembly.](../en/images/d09-05.jpg)

**Pro version: the leader arm uses a 5V6A power adapter, and the follower arm uses a 12V5A power adapter**

Servo ID setup, servo angle calibration and assembly must be done beforehand; refer to the [official assembly tutorial](https://huggingface.co/docs/lerobot/so101)

<sheet sheet-id="kN3ZzK" token="DDCXsU4TCh4wpytxOAkcO9u8nsc"></sheet>

# Step 1: Set Servo IDs and Install the Servo Horns (except Servo 5)

<grid>
<column width-ratio="0.500000">
![The image shows the Feetech host debugging tool interface. The interface has three tabs, "Debug," "Program" and "Upgrade," with "Program" currently selected. Key information: 1. In the communication settings, the port number is COM6 and the baud rate is 1000000; 2. In the servo operations, synchronous write, asynchronous write and torque output are all checked; 3. In the servo feedback, parameters such as voltage, current, temperature and position all show 0; 4. In the servo search, id 1 is selected, model ST53215. This image relates to the debugging operations described above, such as setting servo IDs and installing the servo horn, and presents the debugging tool interface.](../en/images/d09-06.png)
</column>
<column width-ratio="0.500000">
![The image shows the Feetech host debugging tool interface, used to set servo IDs. The interface has three tabs, "Debug," "Program" and "Upgrade," with "Program" currently selected. In the "Center calibration" area, the ID number is 4, with a "Save" button to the right. The left side of the interface shows the servo ID, model and other information. This image relates to the "Step 1: Set Servo IDs and Install the Servo Horns (except Servo 5)" content in the document and presents the interface of the servo ID setup operation, visually showing where the ID number is set.](../en/images/d09-07.png)
</column>
</grid>

1. Open the Feetech host debugging tool, select the COM port, set the baud rate to one million, and click "Open"
2. Click "Search"; once "STS3215" appears, click "Stop" and then click "STS3215"
3. Select "Debug" at the top; you can drag the slider to rotate the servo, or click "Scan" to make it move back and forth. Confirm the servo runs normally
4. Select "Program" at the top
5. Click "Center calibration" to set the servo's current rotation-shaft position as the center (0-4095)
6. Click "ID", set the corresponding servo's ID number in the lower-right corner, and click "Save". Note that the number is plain Arabic numerals with no letters.
7. Unplug the cable connecting the servo to the control board
8. Plug the servo cable into the servo

Servo 1 gets two cables; the other servos get only one cable for now

![The image shows the servo installation during SO-ARM101 arm kit assembly. The frame contains the follower arm and the leader arm, with the follower arm numbered 123456 and the leader arm numbered 123456. The servos are labeled with gear ratios of 1:345, 1:191 and 1:147. Below is the control board, connected to two cables, one white and one black. This image relates to the assembly steps above and visually presents the servos' mounting positions and numbers, helping the assembler match the servos to the control board accurately.](../en/images/d09-08.png)

<callout emoji="💡">
Again: make sure each servo's joint ID and gear ratio match **SO-ARM101** exactly.
</callout>

Every motor on the bus has a unique ID. New motors usually come with a default ID of `1`. To ensure communication between the motors and the controller works, we first need to set a unique ID for each motor. In addition, the data transmission speed on the bus is determined by the baud rate. To communicate with each other, the controller and all motors need to be configured with the same baud rate; this arm's servos use a baud rate of 100000.

To do this, we first need to connect the controller to each motor in turn so we can configure them. Because we write these parameters into the non-volatile area of the motor's internal memory (EEPROM), this only needs to be done once.

If you are reusing motors from another robot, you may also need to do this step, because the IDs and baud rates may not match.

The video below shows the sequence of steps for setting motor IDs.

## Windows

<figure view-type="Card">[Attachment: 飞特舵机上位机.zip](../en/images/飞特舵机上位机.zip)</figure>

Use the Feetech servo host tool to set servo IDs and calibrate the center. IDs are set from 1 to 6!

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Windows系统.mp4](../en/images/机械臂舵机设置ID-Windows系统.mp4)</figure>

## Linux/Ubuntu and Mac

<callout emoji="💡">
If you need the Feetech servo host tool, refer to the [Feetech servo debugging tool](https://juxitech.feishu.cn/wiki/HllBwhjJ1iayMdkUTGgcyKbgn8g#share-Jvk1dRRl8oY0Skxrt2VczA9jnNb) above
</callout>

First complete the environment setup following the [official LeRobot installation](https://huggingface.co/docs/lerobot/installation) page

<callout emoji="💡">
Remember to activate the virtual environment and enter the corresponding src/lerobot directory
conda activate lerobot
cd lerobot/src/lerobot
</callout>

1. Find the USB port for the arm. To find the correct port for each arm, run the utility script twice::

```Plain Text
lerobot-find-port
```

Example output when identifying the Leader arm port (for example `/dev/tty.usbmodem575E0031751` on a Mac, or possibly `/dev/ttyACM0` on Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM1
Reconnect the USB cable.
```

Example output when identifying the Follower arm port (for example `/dev/tty.usbmodem575E0032081`, or possibly `/dev/ttyACM1` on Linux):

```PowerShell
Finding all available ports for the MotorBus.
['/dev/ttyACM0', '/dev/ttyACM1']
Remove the usb cable from your MotorsBus and press Enter when done.

[...Disconnect corresponding leader or follower arm and press Enter...]

The port of this MotorsBus is /dev/ttyACM0
Reconnect the USB cable.
```

<callout emoji="💡">
Remember to unplug the USB connector, otherwise the port cannot be detected.
</callout>

2. Connect the PC to the follower arm's servo driver board with a USB cable and power it on. Then run the following command. Change --robot.port=/dev/ttyACM0 in the command to the port you found. For example, if the port you found is /dev/ttyACM1, change it to --robot.port=/dev/ttyACM1

```Python
lerobot-setup-motors \
    --robot.type=so101_follower \
    --robot.port=/dev/ttyACM0
```

You will see the following output.

```Python
Connect the controller board to the 'gripper' motor only and press enter.
```

Following the instructions, connect the gripper servo. Make sure it is the only servo connected to the servo driver board and that this servo is not yet connected to any other servo. After you press **[Enter]**, the script automatically sets that servo's ID and baud rate. IDs are set from 6 to 1!

After that, you should see the following:

```Python
'gripper' motor id set to 6
```

Then the next output is:

```Python
Connect the controller board to the 'wrist_roll' motor only and press enter.
```

<callout emoji="❗">
**Note** Repeat the above for each servo, following the instructions.
As with the previous servos, make sure it is the only servo connected to the driver board and that the servo itself is not connected to any other servo.
</callout>

Before pressing **Enter** each time, be sure to check your cable connections. For example, the power cable may come loose while handling the circuit board.

When you have completed all the steps, the script ends automatically and the servos are ready to use. You can now connect each servo's 3-pin connector in turn, and connect the cable of the first servo (the "shoulder pan" servo with ID 1) to the driver board. The driver board can now be mounted on the base of the arm.

Repeat the same steps for the leader arm.

```Python
lerobot-setup-motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/ttyACM0
```

<figure view-type="Preview">[Attachment: 机械臂舵机设置ID-Linux系统.mp4](../en/images/机械臂舵机设置ID-Linux系统.mp4)</figure>

# Step 2: Assembly

<callout emoji="💡">
- The assembly steps for the follower arm are essentially the same as for the leader arm. The only difference is that after step 12, the end effector (gripper and handle) is installed differently.
</callout>

<figure view-type="Preview">[Attachment: SO-ARM101机械臂组装教程.mp4](../en/images/SO-ARM101机械臂组装教程.mp4)</figure>

<callout emoji="💡">
Installing the servo driver board: first mount the 4 brass standoffs, then secure the driver board with four M2.5\*8 screws
</callout>

<grid>
<column width-ratio="0.525947">
![Install the four brass standoffs](../en/images/d09-09.webp)
</column>
<column width-ratio="0.474053">
![Secure the servo driver board with M2.5*8 screws](../en/images/d09-10.webp)
</column>
</grid>

![Mount onto the arm and wire it up](../en/images/d09-11.png)

**Pro version: the black leader arm uses a 5V6A power adapter, and the white follower arm uses a 12V5A power adapter**







# Setting Servo IDs and Center Calibration in the Web UI

https://bambot.org/feetech.js?lang=zh

1. Enter 0 or 1 depending on the servo model, then click "Connect"

![The image shows the "Connect" interface in the arm kit assembly tutorial. On the left of the interface is the word "Connect," and on the right are a "Baud rate" dropdown set to 1,000,000 bps (Index 0), and an input box for "Protocol end (0=STS/SMS, 1=SCS)" set to 0, with a red box around the number "1" beside the input box. Below is a green "Connect" button, with a red box around the number "2" beside it. The bottom shows "Status: Disconnected". This image corresponds to the content above, "Enter 0 or 1 depending on the servo model, then click 'Connect'," and visually presents the settings of the connection operation.](../en/images/d09-12.png)

2. Scan servos with IDs 1\~6; use FOUND in the scan results to confirm the corresponding ID servo. For example, in the image servo ID 1 was found

![The image shows the "Scan servos" step interface in the SO-ARM101 arm kit assembly tutorial. At the top of the interface are "Start ID" and "End ID" input boxes, currently with start ID 1 and end ID 6. Below is a "Start scan" button. In the scan results, scanning IDs 1-6 finds no servos, reporting "Exception: No status packet! Error code: 0". This image is closely tied to the context and visually presents the interface and results when scanning for servos, helping users understand the servo scan status.](../en/images/d09-13.png)

3. ID setting and center calibration

① Set the current servo ID input to the scanned servo's ID

② Enter a number in "ID management" and click "Change ID" to set the ID

③ Center calibration (the STS3215 servo center is 2047, the SCS0009 servo center is 511)

STS servo: enter 2047 in "Position control" and click "Set"

SCS servo: enter 511 in "Position control" and click "Set"

![The image shows a single-servo control interface. The current servo ID is 1; after entering the number 1 under ID management and clicking "Change ID," the message "Success: ID changed to 1" appears. Under Position Control the value is 2047, and clicking the "Set" button applies it. This image relates to the "ID setting and center calibration" context and visually presents the interface for the ID setup operation, helping users understand how to enter a number under "ID management" to set the ID and how to enter the center value under "Position control" and click "Set" to finish.](../en/images/d09-14.png)
