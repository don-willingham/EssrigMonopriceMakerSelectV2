# EssrigMonopriceMakerSelectV2
Information and configuration on Essrig Elementary School's Monoprice Maker Select V2

# Hardware
Monoprice Maker Select V2, which is equivalent to a Wanhao Duplicator i3 v2.

# Software

## Cura
At the time of writing [Ultimaker](https://ultimaker.com/) [Cura](https://ultimaker.com/software/ultimaker-cura) 5.2.1 was used.

### Installation
Hillsborough County Schools computers are locked down, and can't run the installer. Download [Ultimaker-Cura-5.2.1-win64.exe](https://github.com/Ultimaker/Cura/releases/download/5.2.1/Ultimaker-Cura-5.2.1-win64.exe) and extract the contents with [7zip](https://www.7-zip.org/). Copy to microUSB card, or thumb drive. Insert card/drive and run `Ultimaker-Cura-5.2.1-win64\Ultimaker-Cura.exe`. Select `Settings` -> `Printer` -> `Manage Printers...`. Select `Add New`. Expand `Add a non-networked printer`. Scroll down to, and expand `Wanhao`. Select `Wanhao Duplicator i3`, and change Printer Name to `EssrigMPMSv2`. Under Preset printers, select `EssrigMPMSv2`.

### Slicing
Select `File`, and `Open File(s)...`, select an .stl file. Set `Profile`, `Infill Density`, 'Printing Temperature` and any other settings. If printer is on, select `Release SD` from main menu. Remove microSD card from printer. Insert microSD card to adapter, and adapter into computer. (Ensure any lock switch is not selected) Select `Slice`, `Save to Removable ...`, then `Eject`.

# Printing

## Preparation
Clean bed with isopropyl alcohol. Mist a little hair spray on the bed, if prints don't stick.

## From SD
Insert microSD card with gcode on it. Press the button, scroll down to `Print from SD`, you man need to scroll down to `Refresh`, then select your file, and press button. Pay close attention to the first layers. If necessary, select `Tune` and `Babystep Z`, then turn the knob to adjust the nozzle height. Plus is up, minus is down.

# Hardware
Z axis limit switch was replaced with a [Micro Limit Switch, CYT1073 AC 2A 125V 3Pin SPDT Rocker Switches Long Hinge Lever for Arduino (30 Pack) by MUZHI](https://www.amazon.com/dp/B088W8WMTB?ref_=cm_sw_r_cp_ud_dp_VCW0HAEW99HP4Y2WK0T2)


# Firmware
The original Repetier 0.91 was replaced with [TH3D's Unified 2 Firmware for Wanhao/Monoprice “Melzi” Boards](https://support.th3dstudio.com/download/unified-2-firmware-for-wanhao-melzi-boards/), which is based on Marlin 2.52. At first it was configured with just `WANHAO_I3`, but also needed `WANHAO_10K_THERMISTOR` and `WANHAO_10K_BED_THERMISTOR`. The printer name and boot screen have also been customized.

## New Settings
An attempt was made to retain all relevant settings:
```
>>> M503
SENDING:M503
echo:; Linear Units:
echo:  G21 ; (mm)
echo:; Temperature Units:
echo:  M149 C ; Units in Celsius
echo:; Steps per unit:
echo:  M92 X80.00 Y80.00 Z405.46 E96.00
echo:; Max feedrates (units/s):
echo:  M203 X200.00 Y200.00 Z2.00 E50.00
echo:; Max Acceleration (units/s2):
echo:  M201 X1000.00 Y1000.00 Z100.00 E5000.00
echo:; Acceleration (units/s2) (P<print-accel> R<retract-accel> T<travel-accel>):
echo:  M204 P1000.00 R1000.00 T1000.00
echo:; Advanced (B<min_segment_time_us> S<min_feedrate> T<min_travel_feedrate> X<max_x_jerk> Y<max_y_jerk> Z<max_z_jerk> E<max_e_jerk>):
echo:  M205 B20000.00 S0.00 T0.00 X8.00 Y8.00 Z0.30 E5.00
echo:; Material heatup parameters:
echo:  M145 S0 H200.00 B60.00 F0
echo:  M145 S1 H240.00 B100.00 F0
echo:; Hotend PID:
echo:  M301 P19.16 I1.09 D83.97
echo:; Filament load/unload:
echo:  M603 L20.00 U20.00 ; (mm)
```

## Old Settings
The original firmware had the following settings:

```
>>> M205
SENDING:M205
ok 0
EPR:2 75 115200 Baudrate
EPR:3 129 669.157 Filament printed [m]
EPR:2 125 741100 Printer active [s]
EPR:2 79 0 Max. inactive time [ms,0=off]
EPR:2 83 360000 Stop stepper after inactivity [ms,0=off]
EPR:3 3 80.0000 X-axis steps per mm
EPR:3 7 80.0000 Y-axis steps per mm
EPR:3 11 405.4591 Z-axis steps per mm
EPR:3 15 200.000 X-axis max. feedrate [mm/s]
EPR:3 19 200.000 Y-axis max. feedrate [mm/s]
EPR:3 23 2.000 Z-axis max. feedrate [mm/s]
EPR:3 27 40.000 X-axis homing feedrate [mm/s]
EPR:3 31 40.000 Y-axis homing feedrate [mm/s]
EPR:3 35 2.000 Z-axis homing feedrate [mm/s]
EPR:3 39 20.000 Max. jerk [mm/s]
EPR:3 47 0.300 Max. Z-jerk [mm/s]
EPR:3 133 0.000 X home pos [mm]
EPR:3 137 0.000 Y home pos [mm]
EPR:3 141 0.000 Z home pos [mm]
EPR:3 145 200.000 X max length [mm]
EPR:3 149 200.000 Y max length [mm]
EPR:3 153 180.000 Z max length [mm]
EPR:3 51 1000.000 X-axis acceleration [mm/s^2]
EPR:3 55 1000.000 Y-axis acceleration [mm/s^2]
EPR:3 59 100.000 Z-axis acceleration [mm/s^2]
EPR:3 63 1000.000 X-axis travel acceleration [mm/s^2]
EPR:3 67 1000.000 Y-axis travel acceleration [mm/s^2]
EPR:3 71 100.000 Z-axis travel acceleration [mm/s^2]
EPR:0 880 0 Autolevel active (1/0)
EPR:0 106 0 Bed Heat Manager [0-3]
EPR:0 107 255 Bed PID drive max
EPR:0 124 80 Bed PID drive min
EPR:3 108 196.000 Bed PID P-gain
EPR:3 112 33.000 Bed PID I-gain
EPR:3 116 290.000 Bed PID D-gain
EPR:0 120 255 Bed PID max value [0-255]
EPR:3 200 96.000 Extr.1 steps per mm
EPR:3 204 50.000 Extr.1 max. feedrate [mm/s]
EPR:3 208 20.000 Extr.1 start feedrate [mm/s]
EPR:3 212 5000.000 Extr.1 acceleration [mm/s^2]
EPR:0 216 3 Extr.1 heat manager [0-3]
EPR:0 217 230 Extr.1 PID drive max
EPR:0 245 40 Extr.1 PID drive min
EPR:3 218 7.0000 Extr.1 PID P-gain/dead-time
EPR:3 222 2.0000 Extr.1 PID I-gain
EPR:3 226 40.0000 Extr.1 PID D-gain
EPR:0 230 255 Extr.1 PID max value [0-255]
EPR:2 231 0 Extr.1 X-offset [steps]
EPR:2 235 0 Extr.1 Y-offset [steps]
EPR:1 239 1 Extr.1 temp. stabilize time [s]
EPR:1 250 150 Extr.1 temp. for retraction when heating [C]
EPR:1 252 0 Extr.1 distance to retract when heating [mm]
EPR:0 254 255 Extr.1 extruder cooler speed [0-255]

>>> M115
SENDING:M115
Info:External Reset
Info: 0.000000 0.000000 0.000000 0.000000 0.000000 0.000000 0.000000 0.000000 0.000000
Free RAM:10732
ok 0
FIRMWARE_NAME:Repetier_0.91 FIRMWARE_URL:https://github.com/repetier/Repetier-Firmware/ PROTOCOL_VERSION:1.0 MACHINE_TYPE:Mendel EXTRUDER_COUNT:1 REPETIER_PROTOCOL:2
Printed filament:669.16m Printing time:8 days 13 hours 51 min
```

# References
[Manual](https://downloads.monoprice.com/files/manuals/13860_Manual_151111.pdf), however, anything related to the screen and firmware will not be accurate. Ultimaker Cura 5.2.1 is much different than the "pre-Ultimaker?" 15.04.2 version that is in the manual.
[Marlin Firmware](https://marlinfw.org/)

