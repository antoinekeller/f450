# f450 drone

## PX4 build

Clone the PX4 Autopilot repo :
```
git clone https://github.com/PX4/PX4-Autopilot.git
cd PX4-Autopilot
git submodule update --init --recursive
```

Build px4 software for Pixhawk 2.4.8 with CRSF support

```
make px4_fmu-v3_default
```

Then upload your `boards/px4/fmu-v3/default.px4board` to the flight controller via QGroundControl.

or


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

If you need to change something in the config, open the NuttX menu :
```
```
make px4_fmu-v3_default menuconfig
```

## PX4 params

See f450.params

### ELRS

Enable ELRS/CRSF on Telem2 (for example)

```
RC_CRSF_PRT_CFG = TELEM 2
RC_CRSF_TEL_EN = Enabled
```

### Music sound via buzzer

I could not find a way to change the music sound of the ESC, this is why I used the buzzer than you can easily connect to the PixHawk.

To have the Mario theme, write a file in the SD card of Pixhawk

`etc/extras.txt` :

```
tune_control stop
sleep(0.5)
tune_control play -m MFT150e6e6e5c10e4g6
```

## Rates tuning

Default parameters creates a very safe and sloppy, I wanted something more reactive in thrust :

```
MPC_ACC_UP_MAX 6.0
MPC_LAND_SPEED 2.5
MPC_TKO_SPEED 3.0
MPC_Z_VEL_ALL 5.0
MPC_Z_P 1.40
MPC_Z_VEL_MAX_DN 3.8
MPC_Z_VEL_MAX_UP 5.0
MPC_W_VEL_P_ACC 6.0
MPC_Z_V_AUTO_DN 3.8
MPC_Z_V_AUTO_UP 5.0
```

I didnt change the attitude rates, they were just fine.

## RC binding

If you have an ELRS RC (like Radiomaster Zorro), binding to the ELRS receiver is seamless.

