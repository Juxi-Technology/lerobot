[English](../../en/04-teleoperation/mac.md) | [简体中文](../../zh-hans/04-teleoperation/mac.md) | [繁體中文](../../zh-hant/04-teleoperation/mac.md) | Deutsch | [Español](../../es/04-teleoperation/mac.md) | [Français](../../fr/04-teleoperation/mac.md) | [Italiano](../../it/04-teleoperation/mac.md) | [日本語](../../ja/04-teleoperation/mac.md) | [한국어](../../ko/04-teleoperation/mac.md) | [Português (BR)](../../pt-br/04-teleoperation/mac.md) | [Português (PT)](../../pt-pt/04-teleoperation/mac.md)

# Mac-Rechner

## Berechtigungen für den Port erteilen

Geben Sie allen Benutzern Lese- und Schreibberechtigung für diese seriellen Geräte

```Shell
chmod 666 /dev/tty.*
```

## Die Portnummern überprüfen

Follower-Arm:

/dev/tty.usbmodem5AAF2193061

/dev/tty.wchusbserial5AAF2193061

Leader-Arm:

/dev/tty.usbmodem5AAF2194741

/dev/tty.wchusbserial5AAF2194741

## Teleoperation

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5AAF2193061 \
    --robot.id=my_follower_arm \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5AAF2194741 \
    --teleop.id=my_leader_arm
```

## Der andere Port funktioniert auch

```Shell
lerobot-teleoperate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.wchusbserial5AAF2193061 \
    --robot.id=my_follower_arm \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.wchusbserial5AAF2194741 \
    --teleop.id=my_leader_arm
```
