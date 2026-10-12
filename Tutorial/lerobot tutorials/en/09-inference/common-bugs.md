English | [简体中文](../../zh-hans/09-inference/common-bugs.md) | [繁體中文](../../zh-hant/09-inference/common-bugs.md) | [Deutsch](../../de/09-inference/common-bugs.md) | [Español](../../es/09-inference/common-bugs.md) | [Français](../../fr/09-inference/common-bugs.md) | [Italiano](../../it/09-inference/common-bugs.md) | [日本語](../../ja/09-inference/common-bugs.md) | [한국어](../../ko/09-inference/common-bugs.md) | [Português (BR)](../../pt-br/09-inference/common-bugs.md) | [Português (PT)](../../pt-pt/09-inference/common-bugs.md)

# Common Bugs and Fixes

## Camera capture fails

![This image shows the terminal output when LeRobot robot code runs. The `INFO` logs show the OpenCV camera opening and the Follower disconnecting; the `ERROR` log points out that in the `camera_opencv.py` file the `read` function raised a `RuntimeError` because of `OpenCVCamera(0) read failed`. The image relates to the "Camera capture fails" issue, visually showing the problem that appears when the code runs and helping to explain the specific cause of the camera-capture failure.](../../en/images/d65-01.png)

Check whether the wrist camera cable is loose, especially the end near the camera — that connector is very prone to poor contact

## Camera disconnects

![This image shows the running interface for the /opt/miniconda/envs/lerobot_smolvla/bin/lerobot-record.py code. At the top it shows the time, process ID and other information; below are code paths and error messages such as /Users/tommy/Downloads/9-lerobot/lerobot-hf/src/lerobot/scripts/lerobot_record.py and "INFO 2024-01-19 13:58:51: a_openvc.py:541 OpenCCamera(0) disconnected.". The key part is "raise TimeoutError" and "TimeOutError: Time out waiting for frame from camera OpenCCamera(0) after 200 ms. Read thread alive: True.", indicating that camera capture failed. The image relates to the "Camera capture fails" issue, visually showing the error.](../../en/images/d65-02.png)

Restart the command line

## Servo communication problem 1

ConnectionError: Failed to sync read 'Present_Position' on ids=[1, 2, 3, 4, 5, 6] after 1 tries. [TxRxResult] There is no status packet!

![This image shows the following.](../../en/images/d65-03.png)

The fix: change every `num_retry` in the code at `lerobot/src/lerobot/motors/motors_bus.py` to 99, especially the one on the line that errors

![This image shows the contents of the `motors_bus.py` code file in the LeRobot project. The `write` method of the `MotorsBusABC` class is highlighted, with the `num_retry` variable changed to `99`. The image relates to the "Servo communication problem 1" section, corresponding to the fix of changing every `num_retry` in the code at `lerobot/src/lerobot/motors/motors_bus.py` to 99, especially the one on the line that errors.](../../en/images/d65-04.png)

## Servo communication problem 2

ConnectionError: Failed to write 'Torque_Enable' on id\_=1 with '0' after 6 tries. [TxRxResult] There is no status packet!

<grid>
<column width-ratio="0.500000">
![This image shows a command-line session in the zsh terminal on macOS. The terminal shows several file paths and code line numbers, such as `/opt/miniconda3/envs/lerobot_smolvla/lib/python3.12/contextlib.py`. Line 587 of the file `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/motors/motors_bus.py` raises a `ConnectionError`, reporting a failed write of `Torque_Enable` on id=1 with no status packet. The image relates to the "Servo communication problem 2" content, visually showing the code's execution at the moment of the error.](../../en/images/d65-05.png)
</column>
<column width-ratio="0.500000">
![This image shows a command-line session in the zsh terminal on macOS. The terminal shows several file paths and code line numbers, such as `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot/utils/decorators.py`. Here, `/Users/tommy/Downloads/9-lerobot/lerobot/src/lerobot](../../en/images/d65-06.png)
</column>
</grid>

Solution: recalibrate the robot arm
