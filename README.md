# f450 drone

```
~/PX4-Autopilot$ make px4_fmu-v3_default upload
[0/1] uploading px4
==========================================================================================================
WARNING: You should uninstall ModemManager as it conflicts with any non-modem serial device (like Pixhawk)
==========================================================================================================
Waiting for bootloader...
Attempting reboot on /dev/serial/by-id/usb-3D_Robotics_PX4_BL_FMU_v2.x_0-if00 with baudrate=57600...
If the board does not respond, unplug and re-plug the USB connector.

Found board id: 9,0 bootloader protocol revision 5 on /dev/serial/by-id/usb-3D_Robotics_PX4_BL_FMU_v2.x_0-if00
Loaded firmware for board id: 9,0 size: 2026140 bytes (97.37%) 

Bootloader version: unknown
Sn: 002f00333533510c37323830
Chip: 20036419
Family: STM32F42x
Revision: ?
Flash: 2080768 bytes
Windowed mode: False

Erase  : [====================] 100.0%
Program: [====================] 100.0%
Verify : [====================] 100.0%
Rebooting. Elapsed Time 15.223
```
