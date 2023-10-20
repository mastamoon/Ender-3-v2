Config'd for TH3D EZABL Pro and settings 

Configuration.h Settings
The below settings should be enabled (uncommented) and set to the settings we have listed below. The values in the large table should be listed in order that they appear in the Configuration.h file to make setting up easier.

Make sure when you set your DEFAULT_MAX_FEEDRATE you set Z to 15 instead of the default of 5.

For Z_PROBE_FEEDRATE_FAST you can use (15*60) instead of (8*60) if your printer can home the Z axis accurately at 15mm/s speed.

#define Z_MIN_ENDSTOP_INVERTING true

#define Z_MIN_PROBE_ENDSTOP_INVERTING true

#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN

#define FIX_MOUNTED_PROBE

//#define PROBE_MANUALLY

#define PROBING_HEATERS_OFF

#define XY_PROBE_FEEDRATE (133*60)

#define Z_PROBE_FEEDRATE_FAST (8*60)

#define Z_PROBE_FEEDRATE_SLOW (Z_PROBE_FEEDRATE_FAST / 2)

#define MULTIPLE_PROBING 2

#define Z_CLEARANCE_DEPLOY_PROBE 5

#define Z_CLEARANCE_BETWEEN_PROBES 3

#define Z_CLEARANCE_MULTI_PROBE 3

#define Z_AFTER_PROBING 5

#define Z_AFTER_HOMING 5

#define Z_PROBE_LOW_POINT -3

#define Z_PROBE_OFFSET_RANGE_MIN -5

#define Z_PROBE_OFFSET_RANGE_MAX 1

#define Z_MIN_PROBE_REPEATABILITY_TEST

#define AUTO_BED_LEVELING_BILINEAR

#define EXTRAPOLATE_BEYOND_GRID

#define Z_SAFE_HOMING

#define HOMING_FEEDRATE_MM_M { (50*60), (50*60), (8*60) }

#define EEPROM_SETTINGS
You will need to make sure software end-stops are DISABLED for Z after adding the probe. This will let you adjust the Z to a negative number for your offset. Add 2 // in front of the MIN_SOFTWARE_ENDSTOP_Z line in your Configuration.h file as shown below.

//#define MIN_SOFTWARE_ENDSTOP_Z
It is NOT recommended to use the #define RESTORE_LEVELING_AFTER_G28 feature as it has caused issues with ABL probes. We advise not using it to avoid inconsistencies with initial Z home height. 

Probing Points
GRID_MAX_POINTS_X is what controls how many points you probe, stick to odd numbers.

#define GRID_MAX_POINTS_X 3
#define GRID_MAX_POINTS_Y GRID_MAX_POINTS_X
Set your probe offsets
Most printed mounts have their offsets on the pages where you download them from. To see the ones we already have you can look in the Configuration_backend.h file from our Unified Firmware to see all the probe offsets that we have programmed into our firmware if you are using a probe mount we already support in the Unified Firmware.

#define NOZZLE_TO_PROBE_OFFSET { -48, -15, 0 }
In this setting the offsets are X, Y, Z. For Example if your offset was -45 on X and 20 on Y your configuration line would read: #define NOZZLE_TO_PROBE_OFFSET { -45, 20, 0 }

NOTE: You should always have the Z offset set to 0 in the firmware. Never enter in your Z offset in the firmware.

Probe Margin (Edge) Settings
PROBING_MARGIN tells the firmware how far from the edge of the bed to probe. Usually 30 works for most machines. Printers with 300+ beds use 45-50 for this setting. Make sure you are not probing directly over screw heads on the bed. If you change the setting to probe further in or out on the bed but make sure your probe is 100% on the bed with about 10mm from the edge to spare for the best reading.

#define PROBING_MARGIN 30
Other Recommended Settings
#define INDIVIDUAL_AXIS_HOMING_MENU
Configuration_adv.h Settings
The below settings should be enabled (uncommented) and set to the settings we have listed below.

#define BABYSTEPPING

#define DOUBLECLICK_FOR_Z_BABYSTEPPING

#define DOUBLECLICK_MAX_INTERVAL 2000
If you want to combine the ZOffset with Babystepping enable this line:

#define BABYSTEP_ZPROBE_OFFSET
If you have a Graphical LCD and want a fancier babystepping menu enable this line:

#define BABYSTEP_ZPROBE_GFX_OVERLAY