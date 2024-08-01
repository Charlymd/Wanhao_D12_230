# Wanhao_D12_230
Repo for specific Wanhao D12 configuration to build Marlin firmware
You can find latest firmware sources on Marlin Guthub : https://github.com/MarlinFirmware/Marlin

Adaptated configuration for Wanhao D12 230 duplicator
 * With MKS Robin nano 3.1,
 * Touchscreen MKS_TS35_V2_0 (rotate 180°),
 * TMC2209 x5 (native UART communication, no need to set potentiometer)
 * 2 extruders,
 * and BL Touch

 Stepper are :
 * X : BJ42D15-26V41
 * Y : BJ42D15-26V41
 * Z : BJ42D22-23V20
 * E1 : BJ42D22-23V20
 * E2 : BJ42D22-23V20
-------------

Each specific line inside .h files is prefix with comment "Custom config" 

# Configuration.h
#define SERIAL_PORT **-1**
#define MOTHERBOARD **BOARD_MKS_ROBIN_NANO_V3**
#define EXTRUDERS **2**

#define DEFAULT_Kp **18.67**
#define DEFAULT_Ki  **1.08**
#define DEFAULT_Kd **80.53**

#define **USE_XMIN_PLUG**
#define **USE_ZMIN_PLUG**
#define **USE_YMAX_PLUG**

#define X_MIN_ENDSTOP_INVERTING **true**
#define Z_MIN_ENDSTOP_INVERTING **false**
#define Y_MAX_ENDSTOP_INVERTING **true**

#define X_DRIVER_TYPE **TMC2209**
#define Y_DRIVER_TYPE **TMC2209**
#define Z_DRIVER_TYPE **TMC2209**
#define E0_DRIVER_TYPE **TMC2209**
#define E1_DRIVER_TYPE **TMC2209**

#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, **400** }
#define NOZZLE_TO_PROBE_OFFSET **{ -45, -6, 2  }**  // relative position of BL touch
#define PROBING_MARGIN **23**

#define INVERT_E0_DIR **false**
#define INVERT_E1_DIR **false**

#define X_HOME_DIR **-1**
#define Y_HOME_DIR **1**
#define Z_HOME_DIR **-1**

#define X_BED_SIZE **220** // useable area
#define Y_BED_SIZE **220**

#define X_MAX_POS **234**
#define Y_MAX_POS **234**
#define Z_MAX_POS **234**

#define FILAMENT_RUNOUT_SENSOR (TODO)

#define PREHEAT_2_LABEL       **"PETG"**
#define PREHEAT_2_TEMP_HOTEND 230
#define PREHEAT_2_TEMP_BED     70
#define PREHEAT_2_TEMP_CHAMBER 35
#define PREHEAT_2_FAN_SPEED     0

#define DISPLAY_CHARSET_HD44780 **WESTERN**
#define **MKS_TS35_V2_0**
#define TFT_ROTATION **TFT_ROTATE_180** // for installation with rotative button on left

# Configuration_adv.h
#define ADVANCED_PAUSE_FEATURE
#if AXIS_IS_TMC(X)
    #define X_CURRENT       **600**  // set current of TMC2209 via UART channel to prevent overheat
#if AXIS_IS_TMC(Y)
    #define Y_CURRENT       **600**
#define **MONITOR_DRIVER_STATUS**
#define **TMC_DEBUG**