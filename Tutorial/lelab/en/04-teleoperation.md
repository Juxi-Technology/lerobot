English | [简体中文](../zh-hans/04-teleoperation.md) | [繁體中文](../zh-hant/04-teleoperation.md) | [Deutsch](../de/04-teleoperation.md) | [Español](../es/04-teleoperation.md) | [Français](../fr/04-teleoperation.md) | [Italiano](../it/04-teleoperation.md) | [日本語](../ja/04-teleoperation.md) | [한국어](../ko/04-teleoperation.md) | [Português (BR)](../pt-br/04-teleoperation.md) | [Português (PT)](../pt-pt/04-teleoperation.md)

# 4 · Teleoperation

> **Previous:** [03 Connect and calibrate](03-calibration.md)
> **Next:** [05 Record a dataset](05-record-dataset.md)

You move the leader arm by hand; the follower copies the motion. This is how you record demonstrations, and the quickest way to confirm calibration.

## Running it

1. Open the **Teleoperation** tab.
2. Confirm the ports and calibration profile — LeLab remembers those from calibration.
3. Start teleoperation.
4. Move the leader arm.

The tab streams joint positions while it runs. Press stop when done.

**Stop is what parks the follower.** Closing the tab or killing the process leaves the arm where it is.

## What to check

| Check | Why |
|---|---|
| The follower tracks smoothly, without lag or jitter | Rough tracking becomes unusable training data |
| The follower's range matches the leader's | Stopping short or hitting a limit means a joint is miscalibrated — go back to [page 3](03-calibration.md) |
| Both arms move in the same direction | An inverted follower means a joint was calibrated in the wrong direction |
| Nothing collides at the extremes | Move through the full range you plan to use |

If the motion is wrong but not broken — offset, one joint inverted, short of range — recalibrate rather than compensating. A miscalibrated arm produces a dataset that trains the policy to do the wrong thing.

## Cameras

If cameras are configured, the teleoperation view shows their previews.

- Wrist camera: does it show the gripper and what it is about to grasp?
- Fixed camera: does it show the whole workspace?
- Is either image sideways or upside down? Fix the **rotation** on the [calibration tab](03-calibration.md) before recording.

Frames recorded during teleoperation are the only thing the policy ever sees.

---

> **Next:** [05 Record a dataset](05-record-dataset.md)
